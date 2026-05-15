# 03 Priority Map to Layout Spec

## 任务

读取 PRD、Intent 和 Priority Map，生成 Layout Spec。

## 执行前请读取

```text
docs/process_rules.md
docs/workflow.md
execution/03_priority_map_to_layout_spec.md
rules/layout_spec_rules.md
rules/harness_rules.md
```

## 输入

```text
workspace/PRD/{prd_file}.md
workspace/intents/{page_id}.md
workspace/priority_maps/{page_id}.md
```

## 输出

```text
workspace/layout_specs/{page_id}.md
```

## 执行要求

1. 同时参考 PRD、Intent 和 Priority Map，将 Priority Map 中的元素组织为可见布局模块。
2. 每个模块必须标注 P0/P1/P2/P3。
3. 每个模块必须写清关键内容和 PRD 约束。
4. 不写高保真视觉样式。
5. 按 `rules/harness_rules.md` 执行 Layout Gate。
