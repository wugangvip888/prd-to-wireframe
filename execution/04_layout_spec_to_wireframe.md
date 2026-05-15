# Layout Spec to Wireframe

## 目标

读取 PRD、Intent、Priority Map 和 Layout Spec，先完成 Wireframe Preflight Gate，再在 Figma 中生成线框图。

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
生成模式：typical_state / full_state
```

## 执行前请读取

```text
rules/layout_spec_rules.md
rules/wireframe_rules.md
rules/structure_preparation_rules.md
rules/harness_rules.md
execution/wireframe_construction_method.md
```

## 输出

```text
Figma 中更新后的线框图 Frame
新 Frame ID
workspace/records/run_xxx.md
```

## 执行步骤

1. 读取 Layout Spec、wireframe_rules、structure_preparation_rules 和 wireframe_construction_method。
2. 读取 `workspace/figma_targets.md`，确认 Figma 地址和 Figma 内部图层名称。
3. 读取 PRD、Intent 和 Priority Map，按 `rules/harness_rules.md` 执行 Wireframe Preflight Gate。
4. 默认覆盖 Figma 内部图层名称对应的线框图内容；只有用户明确要求保留旧版时，才新建副本或追加版本。
5. 按 Page Frame → Module Frame → Control Frame → Element 建立线框图。
6. 按 P0/P1/P2/P3 表达灰阶、尺寸、边界强弱和显著性。
7. 检查一个 Frame 是否只表达一个页面状态。
8. 检查 PRD 强约束是否在画布可见内容中被表达。
9. 按 `rules/structure_preparation_rules.md` 检查组件候选、Token 采样父级和 Pattern 候选边界。
10. 输出 Figma 地址、Figma 内部图层名称和新 Frame ID，并新增 run record。

## Run Record 变更字段

```text
变更对象：
变更前：
变更后：
变更原因：
依据来源：PRD / Intent / Priority Map / Layout Spec / 人工审核
是否影响上游文件：
是否沉淀为通用规则：
```

## Run Record Figma 字段

```text
Figma 地址：
Figma 内部图层名称：
生成模式：
新 Frame ID：
Frame 名称：
```

## 重跑策略

```text
Figma Wireframe：默认覆盖 Figma 内部图层名称对应的线框图内容。
Run Record：不得覆盖旧记录，每次执行必须新增 run_xxx.md。
旧版线框图：仅当用户明确要求保留时，才在 Figma 中新建副本或追加版本。
```
