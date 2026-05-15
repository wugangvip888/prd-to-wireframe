# PRD to Intent

## 目标

从 PRD 为每个页面生成 Intent。

## 输入

```text
workspace/PRD/{prd_file}.md
```

## 执行前请读取

```text
docs/workflow.md
rules/intent_rules.md
rules/harness_rules.md
```

## 输出

```text
workspace/intents/{page_id}.md
```

## 执行步骤

1. 通读 PRD，识别页面名称和页面数量。
2. 针对每个页面提取页面目标、用户首要任务、主操作、次要入口、关键状态和 PRD 硬约束。
3. 按 `rules/intent_rules.md` 的固定字段生成 Intent。
4. 执行 PRD → Intent 强约束自检。
5. 按 `rules/harness_rules.md` 执行 Intent Gate。
6. 写入 `workspace/intents/`。
