# Layout Spec Rules

## 格式

每个模块使用以下格式：

```text
[module_id]        P0/P1/P2/P3 / 位置或属性
                   关键内容描述
                   PRD约束：xxx
```

## 模块规则

```text
Layout Spec 必须同时参考 PRD、Intent 和 Priority Map。
每个模块必须对应一个可见布局区块。
模块 ID 使用 snake_case。
模块命名表达功能，不表达位置。
交互规则是模块属性，不应伪装成独立布局模块。
模块数量保持精简，能合并的合并。
每个模块必须继承 Priority Map 中的 P0/P1/P2/P3 分级。
```

## 描述规则

```text
描述应服务线框图生成，避免高保真视觉细节。
关键状态必须写清楚，例如空态、加载态、键盘态、禁用态。
页面级约束只有影响线框图表达时才写入 Layout Spec。
界面展示文案以 PRD 为准，不自行改写、缩写或翻译。
```

## 自检

```text
PRD 强约束是否进入模块描述。
Intent 的视觉重心是否映射为 P0/P1 模块。
Priority Map 中的元素是否都被覆盖或明确排除。
Layout Spec 是否足以生成一个页面状态一个 Frame 的线框图。
```
