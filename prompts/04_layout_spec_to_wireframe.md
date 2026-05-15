# 04 Layout Spec to Wireframe

## 任务

读取 PRD、Intent、Priority Map 和已确认的 Layout Spec，先执行 Wireframe Preflight Gate，再根据指定 Figma 地址和内部图层名称生成线框图 Frame。

## 执行前请读取

```text
docs/process_rules.md
docs/workflow.md
execution/04_layout_spec_to_wireframe.md
execution/wireframe_construction_method.md
rules/layout_spec_rules.md
rules/wireframe_rules.md
rules/structure_preparation_rules.md
rules/harness_rules.md
```

## 输入

```text
workspace/layout_specs/{page_id}.md
workspace/PRD/{prd_file}.md
workspace/intents/{page_id}.md
workspace/priority_maps/{page_id}.md
workspace/figma_targets.md
Figma 地址
Figma 内部图层名称
本次生成页面范围
重跑策略：默认覆盖 Figma 内部图层名称对应的线框图内容
```

## 输出

```text
Figma 中更新后的线框图 Frame
新 Frame ID
workspace/records/run_xxx.md
```

## 执行要求

1. 默认覆盖 `workspace/figma_targets.md` 中 Figma 内部图层名称对应的线框图内容；只有用户明确要求保留旧版时，才新建副本或追加版本。
2. 读取 `workspace/figma_targets.md`，确认 Figma 地址和 Figma 内部图层名称。
3. 生成前按 `rules/harness_rules.md` 执行 Wireframe Preflight Gate。
4. 通过 Preflight 后，按 Page Frame → Module Frame → Control Frame → Element 构造。
5. 按 P0/P1/P2/P3 表达信息层级。
6. 按 `rules/structure_preparation_rules.md` 保留组件候选、Token 采样父级和 Pattern 候选所需结构边界。
7. 检查一个 Frame 是否只表达一个页面状态。
8. 输出 Figma 地址、Figma 内部图层名称、新 Frame ID、生成结果摘要，并新增 Wireframe 后变更记录。
