# Priority Map to Layout Spec

## 目标

将页面 Intent 和 Priority Map 转成可生成线框图的 Layout Spec。

## 输入

```text
workspace/PRD/{prd_file}.md
workspace/intents/{page_id}.md
workspace/priority_maps/{page_id}.md
```

## 执行前请读取

```text
rules/priority_rules.md
rules/layout_spec_rules.md
rules/harness_rules.md
```

## 输出

```text
workspace/layout_specs/{page_id}.md
```

## 执行步骤

1. 读取 PRD、Intent 和 Priority Map。
2. 将 P0/P1/P2/P3 元素组织为可见布局模块。
3. 为每个模块写入模块 ID、权重、位置或属性、关键内容描述和 PRD 约束。
4. 检查 Priority Map 中的元素是否被覆盖或明确排除。
5. 检查 Layout Spec 是否足以生成 Figma 线框图。
6. 按 `rules/harness_rules.md` 执行 Layout Gate。
