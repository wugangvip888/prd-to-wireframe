# Wireframe Rules

## 目标

线框图必须是一套可支撑后续工作的结构化骨架，而不只是视觉草图。

后续可支撑对象：

```text
真实设计稿绘制
Auto Layout 搭建
命名系统参考
组件候选识别
Token / Pattern 采样参考
AI 后续生成页面时的结构输入
```

## 输出单位

```text
一个页面在一个具体状态下的完整 Frame。
```

规则：

```text
一个 Frame 只表达一个页面状态。
不把多个页面状态压进同一个 Frame。
不把流程说明混入页面 Frame。
不把组件状态展示混入页面 Frame。
需要作为后续设计、命名、组件、Token 或 Pattern 参考的页面级状态，必须拆成独立 Frame。
仅用于流程理解的状态集合，只能作为说明草图，不得进入标准线框图输入区。
```

## Page Frame 命名规则

统一格式：

```text
[page_number]_[page_name]_state_[state_value]
```

要求：

```text
必须保留真实页面编号。
必须显式写 state。
默认态必须写 state_default。
状态值必须是语义词，不允许位置词、临时词或无意义数字。
不允许中文命名。
不允许无语义数字尾缀。
```

示例：

```text
01_homepage_state_default
02_text_result_state_empty
07_doc_translation_state_uploading
```

禁止：

```text
首页
homepage_1
page_left
02_text_result_default
frame_12
```

## 页面身份与标题图层规则

```text
Page Frame 名称负责表达页面和状态身份。
顶部导航可见标题使用 nav_title。
顶部导航可见副标题使用 nav_subtitle。
页面主体中真实存在的内容标题可使用 content_title 或具体模块语义命名。
不得额外生成通用 page_title 图层。
不得同时使用 page_title 和 nav_title 表达同一标题。
不得同时使用 page_subtitle、subtitle_mode 或 nav_subtitle 表达同一副标题。
```

说明：

```text
如果标题属于顶部导航，统一命名为 nav_title。
如果副标题属于顶部导航，统一命名为 nav_subtitle。
如果标题属于模块内容，命名应跟随模块语义，例如 outline_title_label、sheet_title。
如果页面身份已由 Page Frame 名称表达，不再创建额外标题图层。
同一可见副标题只能保留一个语义图层；如果 page_subtitle 与 subtitle_mode 内容重复，删除重复项并统一收敛为 nav_subtitle。
```


## Page Frame 尺寸规则

默认移动端线框图 Page Frame 使用：

```text
width: 360
height: 780
```

规则：

```text
同一批标准页面 Frame 必须保持相同尺寸。
除非 PRD 明确要求其他设备规格，不得为单个页面临时改变 Page Frame 尺寸。
如果 PRD 明确要求平板、桌面端、横屏或特殊容器，应先在 Layout Spec 中记录目标设备和尺寸依据，再生成对应 Frame。
线框图尺寸用于结构表达和后续设计衔接，不代表最终适配断点或高保真视觉尺寸。
```

## 页面区排布规则

标准页面区只放可作为后续设计、命名、组件、Token 或 Pattern 输入的独立页面 Frame。

默认排布：

```text
排列方向：横向排列
顶边位置：y = 0
默认起点：x = 0
Frame 间距：40
默认 x 步进：400
默认尺寸：360 x 780
```

规则：

```text
所有标准页面 Frame 顶边必须对齐。
同一页面多状态必须相邻排列。
不同页面按页面编号或用户确认的页面顺序排列。
页面区不混入说明草图。
页面区不混入组件参考内容。
页面区不混入废弃 Frame。
组件参考区如需预留，必须与标准页面区分离，不得作为当前阶段正式输出。
```

## 系统 UI 与安全区规则

默认线框图不主动生成以下系统 UI 或占位：

```text
状态栏
灵动岛
刘海屏占位
Home Indicator
系统导航栏
安全区占位
设备外壳
```

例外：

```text
只有 PRD 明确要求状态栏适配、灵动岛适配、系统 UI 避让、安全区表达或固定系统区域时，才允许在线框图中表达。
允许表达时，必须在 Layout Spec 中写明依据，并在线框图中作为 P3 或页面结构约束处理。
系统 UI / 安全区表达不得成为装饰元素，不得抢占 P0/P1 主任务层级。
```

## 页面内部层级

页面内部按 4 层组织：

```text
Page Frame
  Module Frame
    Control Frame
      Element
```

解释：

```text
Page Frame：页面状态容器。
Module Frame：页面级功能模块或稳定功能分区。
Control Frame：可交互控件或稳定局部结构。
Element：文本、描边、图形、占位内容。
```

禁止跳层乱放：

```text
页面下直接散放按钮和图标。
控件元素没有父级容器。
同类控件结构深度不一致。
把页面级模块伪装成普通 group。
```

## 哪些对象必须成为 Frame

### 必须是 Page Frame

```text
每个页面状态。
```

### 必须是 Module Frame

满足以下任一条件：

```text
在 Layout Spec 中是独立模块。
在页面中承担明确功能分区。
后续设计稿中需要整体做 Auto Layout。
会被整体移动、替换、复用。
会作为组件、Token 或 Pattern 采样的结构上下文。
```

### 必须是 Control Frame

满足以下任一条件：

```text
可点击。
有“背景 + 图标/文字”组合。
是局部复用单元。
后续设计稿中需要单独调间距、对齐、状态。
会成为组件候选或组件内部结构。
```

### 不必单独成 Frame

```text
纯文本占位。
单根分割线。
纯装饰矩形。
图标内部的小线段、小几何。
```

这些对象应放进所属控件或模块内部。

## Module 命名规则

模块使用：

```text
snake_case
```

要求：

```text
名称表达功能，不表达位置。
名称稳定，不带临时数字。
同语义模块跨页面尽量同名。
优先表达结构归属，例如 input_actions 优于 quick_actions。
```

禁止：

```text
left_area
module_1
top_group
box_23
```

## Control 命名规则

控件优先使用以下格式：

```text
[semantic_name]_action
[semantic_name]_button
[semantic_name]_cta
[semantic_name]_icon
[semantic_name]_capsule
[semantic_name]_tab
[semantic_name]_card
[semantic_name]_input
```

要求：

```text
优先使用语义词，不使用坐标词。
同一控件跨页面复用时尽量保持同名。
控件名称必须能对应 PRD、Intent、Priority Map 或 Layout Spec 中的功能语义。
```

禁止：

```text
source_read_icon_92
copy_icon_186
icon_left
button_top
group_12
```

## Element 命名规则

常用元素命名：

```text
label
value
placeholder
helper_text
divider
container_bg
button_bg
capsule_bg
icon_container
```

要求：

```text
Element 命名表达元素角色，不表达坐标。
胶囊控件内部优先使用 capsule_bg、label、icon、icon_container。
按钮控件内部优先使用 button_bg、label、icon_container、xxx_icon。
```

## 文字按钮标准结构

文字按钮或带文字操作控件使用：

```text
xxx_button / xxx_action
xxx_cta
  button_bg（按实际需要）
  label
```

要求：

```text
按钮类控件包括 xxx_button、xxx_action 和 xxx_cta。
如果按钮或操作控件有可见文字，文字必须在按钮背景或按钮 Control Frame 的固定文字框内水平居中。
如果按钮或操作控件有可见文字，文字必须在按钮背景或按钮 Control Frame 的固定文字框内垂直居中。
按钮文字可以使用固定宽度文字框，但不得保持左对齐或顶部对齐。
不得用固定左边距模拟按钮文字位置，除非该按钮同时包含图标且 PRD 或 Layout Spec 明确要求图标 + 文字组合。
只有图标 + 文字组合按钮允许文字相对图标偏移；整体内容组仍必须在按钮容器内视觉居中。
校验按钮文字时，必须检查文字框内文字对齐方式为水平居中和垂直居中。
```

## 图标按钮标准结构

图标按钮使用：

```text
xxx_action
  icon_container
  xxx_icon
```

线框图阶段图标按钮的可见表达：

```text
icon_container = 灰色背景
xxx_icon = 中文功能说明文字
```

要求：

```text
icon_container 必须可见，使用灰色背景表达图标背景容器。
icon_container 必须是单个圆形背景，宽高相等，圆角为宽高的一半。
icon_container 是图标控件唯一可见圆形；父级 xxx_action Frame 只作为结构容器，不得再绘制圆形背景或圆形描边。
xxx_icon 的实际显示内容必须是中文功能说明文字。
中文功能说明文字必须完整表达图标功能，不使用英文缩写、英文占位或无语义符号。
图标说明文字以 PRD 中的功能描述为准，例如返回、朗读、复制、切换、上传入口、语音输入。
图层命名仍保持英文语义命名，例如 back_icon、read_icon、copy_icon、swap_icon。
不允许同一套线框图中并存“有 icon_container 的图标”和“没有 icon_container 的图标”。
不允许双圆形表达方式；同一图标控件内只能有一个圆形图标背景。
```

## 胶囊控件标准结构

胶囊控件使用：

```text
xxx_capsule
  capsule_bg
  label
  icon_container / icon（按实际需要）
```

要求：

```text
胶囊控件必须是 Control Frame。
胶囊控件内部只允许使用 capsule_bg、label、icon_container、icon 这类语义元素命名。
如果胶囊包含下拉、切换、关闭等操作图标，必须按图标按钮或图标元素规则命名。
```

## Tab 控件标准表达

Tab 控件使用：

```text
xxx_tabs
  selected_tab_label
  unselected_tab_label
  selected_indicator
```

线框图阶段可见表达：

```text
选中 Tab：文字字重 600，底部显示黑色色块。
未选中 Tab：文字正常字重。
selected_indicator：width = 10，height = 4，fill = black。
selected_indicator 必须在选中 Tab 固定文字框的水平中心线上对齐。
```

要求：

```text
不得使用方括号表达选中状态，例如 [ AI漫剧生成 ]。
不得用大面积背景块、胶囊背景或灰色按钮样式表达普通 Tab 选中态。
选中态必须由文字字重和 selected_indicator 共同表达。
选中态文字可以使用固定宽度文字框，但文字必须在该文字框内水平、垂直居中。
选中态文字与 selected_indicator 必须作为一个垂直组合处理，二者按固定文字框在水平方向居中对齐。
校验 selected_indicator 时，必须同时校验文字框内文字对齐方式为水平居中和垂直居中。
如果 PRD 明确要求胶囊式子 Tab，才按胶囊控件规则处理；否则按 Tab 控件标准表达。
```

## P0/P1/P2/P3 到线框图表达

```text
P0：最强线框层级，可用更明确边界、更大区域、更深灰阶表达。
P1：核心操作层级，可用标准控件尺寸和清晰边界表达。
P2：辅助层级，可用中灰、较弱边界或较小控件表达。
P3：弱层级，可用浅灰、占位线、弱边界或背景面表达。
```

执行要求：

```text
同一控件类型在同一优先级下应保持一致。
不同优先级导致的尺寸、灰阶或边界差异必须能从 P0/P1/P2/P3 解释。
P0/P1/P2/P3 只表达信息层级、主次关系、操作优先级和状态强弱，不表达最终品牌视觉。
```

## 禁止事项

```text
不得引入品牌色、渐变、阴影、营销风格或最终 UI 风格。
不得把所有模块处理成同一尺寸和同一灰阶。
不得新增 Layout Spec 未要求的导航、图标或操作入口。
不得新增 PRD、Intent、Priority Map 和 Layout Spec 均无法追溯的核心业务能力。
不得用无语义图层名、数字尾缀或位置词替代功能命名。
不得把状态集合草图作为高保真设计、命名系统、组件、Token 或 Pattern 采样输入。
```

## 自检顺序

```text
0. PRD 约束自检：节点是否存在，可见内容是否表达约束。
1. 状态归属：当前 Frame 表达哪个页面、哪个具体状态。
2. 结构一致性：模块是否完整，是否有多余模块，是否符合四层结构。
3. 业务规则：PRD 中的强逻辑约束是否被满足。
4. 命名规则：Page、Module、Control、Element 命名是否符合规则。
5. 复用一致性：跨 Frame 的同类控件、图标、灰阶、尺寸和命名是否一致。
```

命名正确不等于表达正确，必须同时验证画布可见内容。
