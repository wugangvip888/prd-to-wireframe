# 00 Run Full Pipeline

## 任务

从 `workspace/PRD/` 中的当前 PRD 文件开始，自动完成：

```text
PRD
→ Intent
→ Intent Gate
→ Priority Map
→ Priority Gate
→ Layout Spec
→ Layout Gate
→ Wireframe Preflight Gate
→ Figma Wireframe
→ Run Record
```

## 执行前请读取

```text
docs/process_rules.md
docs/workflow.md
execution/00_run_full_pipeline.md
execution/01_prd_to_intent.md
execution/02_intent_to_priority_map.md
execution/03_priority_map_to_layout_spec.md
execution/04_layout_spec_to_wireframe.md
execution/wireframe_construction_method.md
rules/intent_rules.md
rules/priority_rules.md
rules/layout_spec_rules.md
rules/wireframe_rules.md
rules/structure_preparation_rules.md
rules/harness_rules.md
```

## 输入

```text
workspace/PRD/{prd_file}.md
workspace/figma_targets.md
页面范围：全部 / 指定页面
生成模式：typical_state / full_state
```

## 输出

```text
workspace/intents/{page_id}.md
workspace/priority_maps/{page_id}.md
workspace/layout_specs/{page_id}.md
Figma 中更新后的线框图 Frame
workspace/records/run_xxx.md
```

## 执行要求

1. 自动识别当前 PRD 文件和页面范围。
2. 按 Flow 01 生成 Intent，并执行 Intent Gate。
3. 按 Flow 02 生成 Priority Map，并执行 Priority Gate。
4. 按 Flow 03 生成 Layout Spec，并执行 Layout Gate。
5. 读取 `workspace/figma_targets.md`，确认 Figma 地址和 Figma 内部图层名称不为空。
6. 按 Flow 04 执行 Wireframe Preflight Gate。
7. 只有全部 Gate 通过，才生成 Figma Wireframe，并按 `rules/structure_preparation_rules.md` 保留后续组件、Token、Pattern 所需结构边界。
8. 重跑时默认覆盖当前页面的 Intent、Priority Map、Layout Spec 和 Figma 内部图层名称对应的线框图内容。
9. 生成完成后新增 run record，记录输入、输出、Figma 地址、内部图层名称、Frame ID、Gate 结果和变更记录。
10. 任一 Gate 发现 PRD 冲突、关键遗漏或凭空新增时，停止后续步骤，并在 run record 或执行摘要中记录阻塞原因。
11. 每完成一个阶段产物后立即落盘；如果流程中断，必须在 run record 或执行摘要中记录最后成功阶段和恢复入口。
12. 恢复执行时，先读取最近一次相关 run record 和已存在产物，复用已通过 Gate 且未受上游修改影响的产物。
