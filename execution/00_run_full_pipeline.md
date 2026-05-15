# Run Full Pipeline

## 目标

用一次执行完成从 PRD 到 Figma Wireframe 的全流程生成。

## 输入

```text
workspace/PRD/{prd_file}.md
workspace/figma_targets.md
页面范围：全部 / 指定页面
生成模式：typical_state / full_state
```

## 执行前请读取

```text
docs/workflow.md
rules/intent_rules.md
rules/priority_rules.md
rules/layout_spec_rules.md
rules/wireframe_rules.md
rules/structure_preparation_rules.md
rules/harness_rules.md
execution/01_prd_to_intent.md
execution/02_intent_to_priority_map.md
execution/03_priority_map_to_layout_spec.md
execution/04_layout_spec_to_wireframe.md
execution/wireframe_construction_method.md
```

## 输出

```text
workspace/intents/{page_id}.md
workspace/priority_maps/{page_id}.md
workspace/layout_specs/{page_id}.md
Figma 中更新后的线框图 Frame
workspace/records/run_xxx.md
```

## 执行步骤

1. 检查 `workspace/PRD/` 中是否存在当前 PRD 文件。
2. 检查 `workspace/figma_targets.md` 中是否填写 Figma 地址和 Figma 内部图层名称。
3. 通读 PRD，识别页面范围；如果用户未指定页面范围，默认处理全部页面。
4. 对每个页面执行 Flow 01，生成 `workspace/intents/{page_id}.md`。
5. 对每个页面执行 Intent Gate；未通过则停止该页面后续生成。
6. 对通过 Intent Gate 的页面执行 Flow 02，生成 `workspace/priority_maps/{page_id}.md`。
7. 对每个页面执行 Priority Gate；未通过则停止该页面后续生成。
8. 对通过 Priority Gate 的页面执行 Flow 03，生成 `workspace/layout_specs/{page_id}.md`。
9. 对每个页面执行 Layout Gate；未通过则停止该页面 Wireframe 生成。
10. 对通过 Layout Gate 的页面执行 Wireframe Preflight Gate。
11. 只有通过 Wireframe Preflight Gate 的页面，才进入 Figma Wireframe 生成。
12. 按 `execution/wireframe_construction_method.md` 和 `rules/structure_preparation_rules.md` 生成 Figma Frame，保留后续组件、Token、Pattern 所需结构边界。
13. 重跑时默认覆盖当前页面的 Intent、Priority Map、Layout Spec 和 Figma 内部图层名称对应的线框图内容。
14. 新增 `workspace/records/run_xxx.md`，记录输入、页面范围、Gate 结果、Figma 地址、Figma 内部图层名称、Frame ID、人工确认点和 Wireframe 后变更。

## 停止条件

```text
PRD 文件不存在。
Figma 地址为空。
Figma 内部图层名称为空。
PRD 与下游产物发生冲突。
关键页面、关键状态或 PRD 硬约束遗漏。
下游产物凭空新增 PRD 未定义的核心业务能力。
Layout Spec 不足以生成一个页面状态一个 Frame 的线框图。
```

## Run Record 必填字段

```text
run_id：
执行时间：
PRD 输入：
页面范围：
生成模式：
Figma 地址：
Figma 内部图层名称：
Intent 输出：
Priority Map 输出：
Layout Spec 输出：
Gate 结果：
Figma Frame ID：
Frame 名称：
Wireframe 后变更：
人工确认点：
```

## 重跑策略

```text
Intent、Priority Map、Layout Spec：默认覆盖同名 {page_id}.md，保留当前最新产物。
Figma Wireframe：默认覆盖 `workspace/figma_targets.md` 中 Figma 内部图层名称对应的线框图内容。
Run Record：不得覆盖旧记录，每次执行必须新增 run_xxx.md。
旧版线框图：仅当用户明确要求保留时，才在 Figma 中新建副本或追加版本。
```
