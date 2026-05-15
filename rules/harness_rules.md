# Harness Rules

## 目标

Harness 用于在每一步生成后验证产物是否可进入下一步，尤其是在生成 Wireframe 前完成总校验。

## 基本原则

```text
PRD 是最高业务边界。
Intent、Priority Map、Layout Spec 和 Wireframe 不得与 PRD 冲突。
下游产物不得凭空新增 PRD 未定义的核心业务能力。
PRD 中影响页面表达的强约束不得遗漏。
每一步都必须能说明关键判断来自 PRD、Intent、Priority Map 或 Layout Spec。
```

## 分步 Gate

```text
Intent Gate：
检查 Intent 是否覆盖 PRD 中的页面目标、用户任务、关键状态和硬约束。

Priority Gate：
检查 Priority Map 是否同时参考 PRD 和 Intent。
检查 P0/P1/P2/P3 是否服务 Intent，同时不遗漏 PRD 必须出现的元素。

Layout Gate：
检查 Layout Spec 是否同时参考 PRD、Intent 和 Priority Map。
检查 Priority Map 中的元素是否被覆盖或明确排除。
检查模块描述是否足以生成一个页面状态一个 Frame 的线框图。

Wireframe Preflight Gate：
检查 PRD、Intent、Priority Map 和 Layout Spec 四者之间无冲突、无关键遗漏、无凭空新增。
只有通过 Wireframe Preflight Gate，才能进入 Figma Wireframe 生成。
```

## 冲突处理

```text
发现 PRD 与下游产物冲突时，以 PRD 为准，先停止进入下一步。
发现 Intent、Priority Map、Layout Spec 之间冲突时，先指出冲突位置和影响范围。
发现 PRD 有歧义时，不自行补业务结论；在产物或记录中标注待人工确认。
发现遗漏时，优先回补对应上游产物，再继续下游生成。
```

## Wireframe 后变更记录

```text
Wireframe 生成后的任何结构、内容、状态或层级改动，必须写入 workspace/records/run_xxx.md。
记录必须包含：变更对象、变更前、变更后、变更原因、依据来源、是否影响上游文件、是否沉淀为通用规则。
只有跨项目可复用的判断方法才能进入 rules/。
单个项目的页面事实、业务文案、模块位置和临时调整不得进入 rules/。
```

## 重跑策略

```text
重跑同一项目或同一页面时，默认覆盖当前页面的 Intent、Priority Map 和 Layout Spec。
重跑 Wireframe 时，默认覆盖 workspace/figma_targets.md 中 Figma 内部图层名称对应的线框图内容。
run record 不得覆盖；每次执行必须新增 workspace/records/run_xxx.md。
如果用户明确要求保留旧版线框图，才在 Figma 中新建副本或追加版本。
```
