# Workflow

## 主流程

```text
workspace/PRD/{prd_file}.md
→ workspace/intents/{page_id}.md
→ Intent Harness Check
→ workspace/priority_maps/{page_id}.md
→ Priority Harness Check
→ workspace/layout_specs/{page_id}.md
→ Layout Harness Check
→ Wireframe Preflight Check
→ Figma Wireframe
→ workspace/records/run_xxx.md
```

## 执行入口

```text
全流程入口：prompts/00_run_full_pipeline.md
分步入口：prompts/01_prd_to_intent.md → prompts/02_intent_to_priority_map.md → prompts/03_priority_map_to_layout_spec.md → prompts/04_layout_spec_to_wireframe.md
```

默认优先使用全流程入口；需要人工逐步审核时使用分步入口。

## 执行顺序

1. PRD to Intent：识别页面、目标、用户任务和 PRD 硬约束。
2. Intent Harness Check：校验 Intent 是否覆盖 PRD 的页面目标、关键状态和硬约束。
3. Intent to Priority Map：同时参考 PRD 和 Intent，为页面元素标注 P0/P1/P2/P3。
4. Priority Harness Check：校验 Priority Map 是否服务 Intent，且不遗漏 PRD 必须出现的元素。
5. Priority Map to Layout Spec：同时参考 PRD、Intent 和 Priority Map，将权重排序转为可见布局模块。
6. Layout Harness Check：校验 Layout Spec 是否覆盖 Priority Map，并保持 PRD 与 Intent 一致。
7. Wireframe Preflight Check：生成 Wireframe 前，统一校验 PRD、Intent、Priority Map 和 Layout Spec 无冲突、无关键遗漏、无凭空新增。
8. Layout Spec to Wireframe：通过 Preflight 后，按 wireframe_rules 和 structure_preparation_rules 在 Figma 中生成一个页面状态一个 Frame 的线框图。
9. Record：新增记录输入、范围、输出、Frame ID、人工审核点和 Wireframe 后变更。

## 判定优先级

```text
PRD > rules > Intent > Priority Map > Layout Spec > Wireframe
```

PRD 是业务硬边界。rules 约束生成方式，不改写 PRD。

## 生成关系

```text
PRD → Intent
PRD + Intent → Priority Map
PRD + Intent + Priority Map → Layout Spec
PRD + Intent + Priority Map + Layout Spec → Wireframe
```

## Wireframe 生成规则

```text
Frame、尺寸、排布、命名、层级和系统 UI 规则来自 rules/wireframe_rules.md。
组件候选、Token 采样和 Pattern 候选的结构预备规则来自 rules/structure_preparation_rules.md。
默认移动端 Page Frame 尺寸为 360 x 780。
```

## Harness Gate

```text
每一步生成后必须做对应 Harness Check。
Wireframe 生成前必须做 Wireframe Preflight Check。
如果发现冲突、关键遗漏或凭空新增，先停止进入下一步，并回补或标注待人工确认。
```

## 重跑策略

```text
过程产物默认覆盖为最新版本。
Figma Wireframe 默认覆盖 Figma 内部图层名称对应的内容。
workspace/records/run_xxx.md 每次新增，不覆盖旧记录。
```
