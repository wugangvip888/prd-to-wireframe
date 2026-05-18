# 当前文件架构 / Current File Structure

本文档记录 `prd-to-wireframe/` 当前真实存在的项目文件架构。系统文件（如 `.DS_Store`）和 `.git/` 不纳入结构说明。

本项目以 `AI_Design_System/docs/file_structure.md` 为结构样例，但只记录 PRD 到线框图流程所需的目录和核心文件。

## 维护规则

- 本文件只记录当前真实存在的目录和核心文件结构，不记录临时文件、系统文件或运行中间产物。
- 文件和目录在结构树中使用 `英文名（中文名）` 格式，例如 `file_index.md（文件索引）`。
- 只在新增、删除、重命名目录或核心文件时更新本文件；普通内容修改不需要更新。
- `workspace/records/run_xxx.md` 按需展示，默认只展示到记录目录。
- 文件用途的详细说明放在 `docs/file_index.md`，本文件只做结构快照和中文名标注。

```text
prd-to-wireframe/
├── README.md（项目入口说明）
│
├── docs/（项目说明层）
│   ├── file_index.md（文件索引）
│   ├── file_structure.md（当前文件架构）
│   ├── process_rules.md（流程治理规则）
│   ├── self_check.md（自检清单）
│   └── workflow.md（工作流说明）
│
├── prompts/（提示词目录）
│   ├── 00_run_full_pipeline.md（全流程执行提示词）
│   ├── 01_prd_to_intent.md（PRD到Intent提示词）
│   ├── 02_intent_to_priority_map.md（Intent到元素权重排序提示词）
│   ├── 03_priority_map_to_layout_spec.md（权重排序到Layout Spec提示词）
│   └── 04_layout_spec_to_wireframe.md（Layout Spec到线框图提示词）
│
├── rules/（规则层）
│   ├── intent_rules.md（Intent规则）
│   ├── priority_rules.md（页面元素权重排序规则）
│   ├── layout_spec_rules.md（Layout Spec规则）
│   ├── wireframe_rules.md（线框图规则）
│   ├── structure_preparation_rules.md（结构预备规则）
│   └── harness_rules.md（Harness校验规则）
│
├── execution/（执行层）
│   ├── 00_run_full_pipeline.md（全流程执行文档）
│   ├── 01_prd_to_intent.md（PRD到Intent执行文档）
│   ├── 02_intent_to_priority_map.md（Intent到元素权重排序执行文档）
│   ├── 03_priority_map_to_layout_spec.md（权重排序到Layout Spec执行文档）
│   ├── 04_layout_spec_to_wireframe.md（Layout Spec到线框图执行文档）
│   └── wireframe_construction_method.md（线框图构造方法）
│
├── skills/（Skill层）
│   └── prd-to-wireframe/（PRD到线框图Skill）
│       ├── SKILL.md（Skill入口）
│       ├── agents/
│       │   └── openai.yaml（Skill UI元数据）
│       └── references/
│           ├── workflow-map.md（工作流映射）
│           ├── artifact-contract.md（产物契约）
│           └── reuse-and-privacy.md（复用与隐私规则）
│
├── workspace/（当前项目工作区）
│   ├── README.md（工作区说明）
│   ├── figma_targets.md（Figma目标登记）
│   ├── PRD/（PRD输入目录）
│   │   └── {prd_file}.md（当前项目PRD，文件名按项目而定）
│   │
│   ├── intents/（Intent输出目录）
│   ├── priority_maps/（页面元素权重排序目录）
│   ├── layout_specs/（Layout Spec输出目录）
│   └── records/（运行记录目录）
```

## 当前完成状态

```text
docs：workflow、process_rules、file_index、file_structure、self_check 已建立。
prompts：全流程入口，以及 PRD到Intent、Intent到Priority Map、Priority Map到Layout Spec、Layout Spec到Wireframe 四段提示词已建立。
rules：Intent、Priority、Layout Spec、Wireframe、Structure Preparation、Harness 六类规则已建立。
execution：全流程执行文档、四段分步执行文档和线框图构造方法已建立。
skills：PRD 到线框图复用 skill 已建立。
workspace：当前项目工作区已建立；真实 PRD、Figma 目标和生成产物作为本地数据，不纳入共享提交。
```

## 当前空目录

```text
workspace/intents/
workspace/priority_maps/
workspace/layout_specs/
无
```
