# Process Rules

## 分层原则

```text
prompts 只记录 AI 调用入口和任务编排。
execution 只记录执行流程。
rules 只记录判断规则。
records 只记录执行结果和人工确认。
docs 只记录项目级说明。
```

不得在多个层级重复维护同一条规则。

## 执行前读取顺序

```text
1. docs/workflow.md
2. 当前 prompt
3. 对应 execution 文档
4. execution 中列出的 rules 文件
5. 业务输入文件
6. 最近一次相关 records（如存在）
```

如果 docs、execution、rules、records 之间不一致，先指出冲突，再继续执行。

## Harness 执行原则

```text
每一步生成后必须执行对应 Harness Check。
Wireframe 生成前必须执行 Wireframe Preflight Check。
Harness Check 发现 PRD 冲突、关键遗漏或凭空新增时，不进入下一步。
单次项目改动写入 records。
只有跨项目可复用的判断方法才沉淀到 rules。
```

## 断点续跑原则

```text
每完成一个阶段产物，必须立即写入对应 workspace 目录。
全流程执行中断时，必须尽可能写入或补写 workspace/records/run_xxx.md，记录已完成阶段、最后成功阶段、阻塞原因和下一步恢复入口。
恢复执行时，必须先读取最近一次相关 run record，再检查 workspace/intents、workspace/priority_maps、workspace/layout_specs 中已存在的产物。
已通过 Gate 且未受 PRD 或人工修改影响的产物可以复用。
受 PRD、Intent、Priority Map 或 Layout Spec 上游变更影响的下游产物必须重新生成。
不得因为中断而跳过 Harness Gate 或 Wireframe Preflight Gate。
```
