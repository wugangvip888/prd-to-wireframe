# Self Check

本文件用于在执行全流程、修改流程文档或新增核心文件后，检查项目结构和引用是否健康。

## 结构检查

```text
README.md 存在。
docs/file_index.md、docs/file_structure.md、docs/workflow.md、docs/process_rules.md、docs/self_check.md 存在。
prompts/00_run_full_pipeline.md 和 prompts/01-04 分步 Prompt 存在。
execution/00_run_full_pipeline.md、execution/01-04 分步执行文档和 execution/wireframe_construction_method.md 存在。
rules/intent_rules.md、rules/priority_rules.md、rules/layout_spec_rules.md、rules/wireframe_rules.md、rules/structure_preparation_rules.md、rules/harness_rules.md 存在。
workspace/PRD/ 中存在当前 PRD 文件。
workspace/figma_targets.md 存在，且包含 Figma 地址和 Figma 内部图层名称。
workspace/intents/、workspace/priority_maps/、workspace/layout_specs/、workspace/records/ 存在。
```

## 引用检查

```text
README.md 的快速开始入口指向 prompts/00_run_full_pipeline.md。
docs/workflow.md 同时记录全流程入口和分步入口。
prompts/00_run_full_pipeline.md 引用的 docs、execution、rules 文件均存在。
prompts/01-04 引用的 docs、execution、rules 文件均存在。
execution/00_run_full_pipeline.md 引用的 rules 和 execution 文件均存在。
execution/01-04 引用的 rules 文件均存在。
Wireframe 相关 prompt 和 execution 必须引用 rules/wireframe_rules.md、rules/structure_preparation_rules.md 和 execution/wireframe_construction_method.md。
docs/file_index.md 与 docs/file_structure.md 对核心文件的记录一致。
新增、删除、重命名核心文件后，必须同步更新 docs/file_index.md 和 docs/file_structure.md。
```

## 流程检查

```text
全流程入口默认使用 prompts/00_run_full_pipeline.md。
PRD → Intent 后必须执行 Intent Gate。
PRD + Intent → Priority Map 后必须执行 Priority Gate。
PRD + Intent + Priority Map → Layout Spec 后必须执行 Layout Gate。
PRD + Intent + Priority Map + Layout Spec → Wireframe 前必须执行 Wireframe Preflight Gate。
Wireframe 生成时必须同时应用 wireframe_rules.md 和 structure_preparation_rules.md。
任一 Gate 发现 PRD 冲突、关键遗漏或凭空新增时，不进入下一步。
```

## Wireframe 尺寸检查

```text
默认移动端 Page Frame 尺寸为 360 x 780。
同一批标准页面 Frame 必须保持相同尺寸。
除非 PRD 明确要求其他设备规格，不得为单个页面临时改变 Page Frame 尺寸。
如果 PRD 明确要求平板、桌面端、横屏或特殊容器，必须先在 Layout Spec 中记录目标设备和尺寸依据。
```

## 重跑检查

```text
重跑同一页面时，Intent、Priority Map 和 Layout Spec 默认覆盖同名 {page_id}.md。
重跑 Wireframe 时，默认覆盖 workspace/figma_targets.md 中 Figma 内部图层名称对应的线框图内容。
workspace/records/run_xxx.md 每次新增，不覆盖旧记录。
只有用户明确要求保留旧版时，才在 Figma 中新建副本或追加版本。
```

## 断点续跑检查

```text
每完成一个阶段产物后必须立即落盘。
流程中断时必须记录最后成功阶段、已生成产物、阻塞原因和恢复入口。
恢复执行时必须先读取最近一次相关 run record。
恢复执行时必须检查 workspace/intents、workspace/priority_maps、workspace/layout_specs 中已有产物。
已通过 Gate 且未受上游修改影响的产物可以复用。
恢复 Wireframe 前必须重新执行 Wireframe Preflight Gate。
```

## 系统文件检查

```text
.DS_Store、日志文件和 .env 文件不应纳入项目结构说明。
.gitignore 应忽略 .DS_Store、*.log、.env 和 .env.*。
```
