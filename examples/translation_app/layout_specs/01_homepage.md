[nav_bar]          顶部固定/常驻
                   中间展示“360 AI翻译”品牌标识；右侧展示“我的翻译库”入口，小屏可退化为图标。

[input_area]       主区域上部/核心视觉重心
                   到边式浅灰背景输入框，无明显边框；提示文案为“粘贴需要翻译的文本、URL，或手动输入内容”。
                   点击任意输入区域唤起键盘；输入文本或URL后实时翻译，键盘右下角“翻译/go”变为可点击。

[input_actions]    输入框内部右下角
                   上传入口与语音输入入口并列，均按图标控件表达为“灰色图标容器 + 中文功能说明文字”；上传入口点击后从底部弹出文档/图片上传选择；语音入口在首页内闭环处理。

[lang_switch]      输入区底部外部/独立背景色
                   默认展示“英文→中文”；支持点击语言名称弹出语言选择列表，点击切换箭头互换源/目标语言。
                   正确结构为：左侧胶囊“源语言文字 + 下拉箭头”，中间独立语言互换按钮，右侧胶囊“目标语言文字 + 下拉箭头”。
                   键盘弹出时随输入区上移至键盘顶部，避免遮挡。

[shortcut_bar]     输入区下方
                   横向展示“文档翻译 / 图片翻译 / 课堂翻译”三个快捷入口，点击跳转对应独立功能页。
                   每个快捷入口包含图标区域和文字标签；图标区域按“灰色图标容器 + 中文功能说明文字”表达，避免纯几何占位。

[bottom_tabs]      页面底部固定
                   仅包含“首页 / 我的”两个Tab，默认选中首页；点击“我的”跳转我的页面。
                   Tab图标按“灰色图标容器 + 中文功能说明文字”表达，不能只保留文字标签。

## 视觉层级标注

```text
P0：
- input_area
- text_input
- bottom_tabs
- home_tab_active
- mine_tab_inactive

P1：
- lang_switch
- source_language_capsule
- target_language_capsule
- swap_action
- input_actions
- upload_action
- voice_action

P2：
- shortcut_bar
- document_shortcut_card
- image_shortcut_card
- classroom_shortcut_card
- nav_bar
- library_button

P3：
- brand_title
- placeholder
- 背景容器、弱分隔、辅助占位
```

说明：

```text
bottom_tabs 是页面级主导航，升级为P0。
lang_switch 保持P1，视觉层级必须低于bottom_tabs。
```
