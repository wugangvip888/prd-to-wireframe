# 文件索引 / File Index

本文件记录 `prd-to-wireframe` 的目录职责、核心文件用途、生成方式和维护流程。

本项目以 `AI_Design_System/docs/file_index.md` 为结构样例，但只保留 PRD 到线框图所需的流程资产。

## 目录索引

| 路径 | 中文名称 | 作用 | 当前状态 |
|---|---|---|---|
| README.md | 项目入口说明 | 说明项目目标、流程边界、快速开始方式 | 已建立 |
| docs/ | 项目说明层 | 存放文件索引、文件结构、工作流、流程治理规则和自检清单 | 已建立 |
| prompts/ | Prompt 层 | 存放全流程入口 Prompt 和四段分步执行 Prompt | 已建立 |
| rules/ | 规则层 | 存放 Intent、Priority Map、Layout Spec、Wireframe、Structure Preparation 和 Harness 的判断规则 | 已建立 |
| execution/ | 执行层 | 记录每一步怎么执行、输入输出和审核点 | 已建立 |
| workspace/ | 当前项目工作区 | 存放当前项目 PRD、生成结果和运行记录 | 已建立 |
| workspace/PRD/ | PRD 输入目录 | 存放当前项目原始 PRD | 已建立 |
| workspace/figma_targets.md | Figma 目标登记 | 存放当前项目线框图生成的 Figma 地址和内部图层名称 | 已建立 |
| workspace/intents/ | Intent 输出目录 | 每个页面一个 Intent 文件 | 已建立，待生成 |
| workspace/priority_maps/ | 元素权重排序目录 | 每个页面一个 Priority Map 文件 | 已建立，待生成 |
| workspace/layout_specs/ | Layout Spec 输出目录 | 每个页面一个 Layout Spec 文件 | 已建立，待生成 |
| workspace/records/ | 运行记录目录 | 记录每次执行输入、范围、输出和人工确认 | 已建立，待生成 |
| examples/ | 示例目录 | 存放示例项目，帮助理解格式，不作为通用规则 | 已建立 |
| examples/translation_app/ | 翻译 App 示例 | 从旧项目抽取的示例 PRD、Intent、Priority Map 和 Layout Spec | 已建立 |

## 文件索引

### Docs

| English Name | 中文名称 | 路径 | 作用 | 生成方式 | 维护流程 |
|---|---|---|---|---|---|
| file_index.md | 文件索引 | docs/ | 记录目录职责、核心文件用途和维护方式 | 人工维护 | 文档治理 |
| file_structure.md | 当前文件架构 | docs/ | 记录当前真实存在的目录和核心文件结构 | 人工维护 | 文档治理 |
| workflow.md | 工作流说明 | docs/ | 记录 PRD → Intent → Priority Map → Layout Spec → Wireframe 的流程顺序和 Harness Gate | 人工维护 | 文档治理 |
| process_rules.md | 流程治理规则 | docs/ | 定义 prompts、execution、rules、records、docs 的职责边界和读取顺序 | 人工维护 | 文档治理 |
| self_check.md | 自检清单 | docs/ | 定义结构、引用、流程、Wireframe 尺寸、重跑策略、断点续跑和示例使用的健康检查项 | 人工维护 | 文档治理 |

### Prompts

| English Name | 中文名称 | 路径 | 作用 | 生成方式 | 维护流程 |
|---|---|---|---|---|---|
| 00_run_full_pipeline.md | 全流程执行提示词 | prompts/ | 指导 AI 一次完成 PRD 到 Figma Wireframe 和 Run Record 的全流程 | 人工维护 | 全流程 |
| 01_prd_to_intent.md | PRD 到 Intent 提示词 | prompts/ | 指导 AI 从 PRD 生成页面 Intent | 人工维护 | Flow 01 |
| 02_intent_to_priority_map.md | Intent 到元素权重排序提示词 | prompts/ | 指导 AI 同时参考 PRD 和 Intent 生成 P0/P1/P2/P3 页面元素权重排序 | 人工维护 | Flow 02 |
| 03_priority_map_to_layout_spec.md | 权重排序到 Layout Spec 提示词 | prompts/ | 指导 AI 同时参考 PRD、Intent 和 Priority Map 转成 Layout Spec | 人工维护 | Flow 03 |
| 04_layout_spec_to_wireframe.md | Layout Spec 到线框图提示词 | prompts/ | 指导 AI 先执行 Wireframe Preflight，再根据 PRD、Intent、Priority Map 和 Layout Spec 在 Figma 生成线框图 Frame | 人工维护 | Flow 04 |

### Rules

| English Name | 中文名称 | 路径 | 作用 | 生成方式 | 维护流程 |
|---|---|---|---|---|---|
| intent_rules.md | Intent 规则 | rules/ | 定义 Intent 固定字段、写作规则和 PRD 强约束提取方式 | 人工维护 | Flow 01 |
| priority_rules.md | 页面元素权重排序规则 | rules/ | 定义 P0/P1/P2/P3 分级、判断规则和输出格式 | 人工维护 | Flow 02 |
| layout_spec_rules.md | Layout Spec 规则 | rules/ | 定义 Layout Spec 模块格式、模块边界、描述规则和自检规则 | 人工维护 | Flow 03 |
| wireframe_rules.md | 线框图规则 | rules/ | 定义 Frame 输出单位、Page Frame 尺寸、页面排布、层级结构、P0/P1/P2/P3 表达和禁止事项 | 人工维护 | Flow 04 |
| structure_preparation_rules.md | 结构预备规则 | rules/ | 定义线框图如何为组件候选、Token 采样和 Pattern 归纳保留结构边界 | 人工维护 | Flow 04 / 后续L2准备 |
| harness_rules.md | Harness 校验规则 | rules/ | 定义分步 Gate、Wireframe Preflight、冲突处理和变更沉淀规则 | 人工维护 | 全流程 |

### Execution

| English Name | 中文名称 | 路径 | 作用 | 生成方式 | 维护流程 |
|---|---|---|---|---|---|
| 00_run_full_pipeline.md | 全流程执行文档 | execution/ | 定义从 PRD 到 Figma Wireframe 的自动编排、Gate、停止条件和断点续跑 | 人工维护 | 全流程 |
| 01_prd_to_intent.md | PRD 到 Intent 执行文档 | execution/ | 定义从 PRD 生成 Intent 的输入、输出、步骤和自检 | 人工维护 | Flow 01 |
| 02_intent_to_priority_map.md | Intent 到权重排序执行文档 | execution/ | 定义生成 Priority Map 的输入、输出、步骤和 Priority Gate | 人工维护 | Flow 02 |
| 03_priority_map_to_layout_spec.md | 权重排序到 Layout Spec 执行文档 | execution/ | 定义生成 Layout Spec 的输入、输出、步骤和 Layout Gate | 人工维护 | Flow 03 |
| 04_layout_spec_to_wireframe.md | Layout Spec 到线框图执行文档 | execution/ | 定义 Wireframe Preflight、Figma 线框图生成和变更记录要求 | 人工维护 | Flow 04 |
| wireframe_construction_method.md | 线框图构造方法 | execution/ | 定义 Page Frame、Module Frame、Control Frame、Element 的构造顺序和自检顺序 | 人工维护 | Flow 04 |

### Workspace

| English Name | 中文名称 | 路径 | 作用 | 生成方式 | 维护流程 |
|---|---|---|---|---|---|
| {prd_file}.md | 当前项目 PRD | workspace/PRD/ | 当前要生成线框图的 PRD 输入，文件名按项目而定 | 人工维护 | PRD 输入 |
| figma_targets.md | Figma 目标登记 | workspace/ | 记录当前项目线框图生成的 Figma 地址和 Figma 内部图层名称 | 人工维护 / 执行前确认 | Flow 04 |
| {page_id}.md | 页面 Intent | workspace/intents/ | 记录单个页面的目标、首要动作、视觉重心、主要操作和硬约束 | AI 生成 / 人工审核 | Flow 01 |
| {page_id}.md | 页面元素权重排序 | workspace/priority_maps/ | 记录单个页面元素的 P0/P1/P2/P3 分级和原因 | AI 生成 / 人工审核 | Flow 02 |
| {page_id}.md | 页面 Layout Spec | workspace/layout_specs/ | 记录单个页面的可见布局模块、权重、关键内容和 PRD 约束 | AI 生成 / 人工审核 | Flow 03 |
| run_xxx.md | 运行记录 | workspace/records/ | 每次执行新增记录，记录输入来源、执行范围、Figma 地址、Figma 内部图层名称、输出结果、Frame ID、断点续跑信息、人工确认和 Wireframe 后变更 | AI 生成 / 人工审核 | Flow 04 |
| README.md | 工作区说明 | workspace/ | 说明 workspace 目录用途 | 人工维护 | 文档治理 |

### Examples

| English Name | 中文名称 | 路径 | 作用 | 生成方式 | 维护流程 |
|---|---|---|---|---|---|
| PRD.md | 翻译 App 示例 PRD | examples/translation_app/ | 示例项目的 PRD 输入 | 从旧项目复制 | 示例维护 |
| project_rules.md | 示例项目业务规则 | examples/translation_app/ | 存放翻译 App 专属规则，不进入通用规则 | 人工维护 | 示例维护 |
| 01_homepage.md | 首页 Intent 示例 | examples/translation_app/intents/ | 展示 Intent 文件格式 | 从旧项目复制 | 示例维护 |
| 01_homepage.md | 首页 Priority Map 示例 | examples/translation_app/priority_maps/ | 展示 P0/P1/P2/P3 权重排序格式 | 人工生成 | 示例维护 |
| 01_homepage.md | 首页 Layout Spec 示例 | examples/translation_app/layout_specs/ | 展示 Layout Spec 文件格式 | 从旧项目复制 | 示例维护 |

## 维护规则

```text
新增、删除、重命名目录或核心文件时，必须同步更新 docs/file_structure.md。
新增、删除、重命名核心文件或改变文件职责时，必须同步更新 docs/file_index.md。
只修改文件正文内容且不改变职责时，不需要更新 file_index.md 或 file_structure.md。
示例项目中的业务规则不得上升为通用规则，除非已确认可复用于多个项目。
```

## 当前缺口

```text
workspace/PRD/ 用于存放当前项目真实 PRD 文件，文件名按项目而定。
workspace/intents/ 暂无当前项目生成内容。
workspace/priority_maps/ 暂无当前项目生成内容。
workspace/layout_specs/ 暂无当前项目生成内容。
workspace/records/ 暂无运行记录。
尚未建立自动化校验脚本，当前可通过 `prompts/00_run_full_pipeline.md` 做全流程 prompt 编排，并依靠 rules、harness gate 和人工审核控制质量。
```
