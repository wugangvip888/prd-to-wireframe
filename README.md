# PRD to Wireframe

本项目只负责从 PRD 生成结构化线框图。

## 流程

```text
PRD
→ Intent
→ Harness Check
→ Element Priority Map
→ Harness Check
→ Layout Spec
→ Wireframe Preflight Check
→ Figma Wireframe
→ Run Record
```

## 包含

- PRD 到页面 Intent
- PRD + Intent 到页面元素权重排序
- PRD + Intent + Priority Map 到 Layout Spec
- PRD + Intent + Priority Map + Layout Spec 到 Figma Wireframe
- 每一步生成后的 Harness Check
- Wireframe 生成前的 Preflight Check
- 每次执行和 Wireframe 后变更的记录与人工审核清单

## 不包含

- 高保真 UI 设计
- Token 提取
- 组件库建设
- 代码生成
- 设计系统协议沉淀

## 快速开始

1. 将 PRD 文件放入 `workspace/PRD/`。
2. 在 `workspace/figma_targets.md` 填写 Figma 地址和 Figma 内部图层名称。
3. 执行 `prompts/00_run_full_pipeline.md`，自动生成 Intent、Priority Map、Layout Spec、Figma Wireframe 和 Run Record。

## 分步执行

如需人工分步审核，也可以按顺序执行：

1. `prompts/01_prd_to_intent.md`
2. `prompts/02_intent_to_priority_map.md`
3. `prompts/03_priority_map_to_layout_spec.md`
4. `prompts/04_layout_spec_to_wireframe.md`
