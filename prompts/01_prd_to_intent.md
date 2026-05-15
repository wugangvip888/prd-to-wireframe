# 01 PRD to Intent

## 任务

读取 `workspace/PRD/` 中的当前项目 PRD 文件，为每个页面生成 Intent 文件。

## 执行前请读取

```text
docs/process_rules.md
docs/workflow.md
execution/01_prd_to_intent.md
rules/intent_rules.md
rules/harness_rules.md
```

## 输入

```text
workspace/PRD/{prd_file}.md
页面范围：全部 / 指定页面
```

## 输出

```text
workspace/intents/{page_id}.md
```

## 执行要求

1. 先通读 PRD，识别页面名称和页面数量。
2. 针对每个页面分析页面目标、用户首要任务、视觉重心、主要操作、次要目标、关键状态和 PRD 硬约束。
3. 按 `rules/intent_rules.md` 的固定字段写入 Intent。
4. 按 `rules/harness_rules.md` 执行 Intent Gate。
5. 自检 PRD 强约束是否进入 Intent。
