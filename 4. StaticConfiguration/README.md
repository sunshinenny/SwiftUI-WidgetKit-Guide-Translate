# StaticConfiguration Structure

# StaticConfiguration

用以描述无配置项的小组件内容。

****

## 定义

```swift
struct StaticConfiguration<Content> where Content : View
```

>  当内容符合 "视图 "时可用。

## 概述

下面的例子显示了一个显示游戏状态的游戏小部件的配置。

```swift
struct GameStatusWidget: Widget {
    var body: some WidgetConfiguration {
        StaticConfiguration(
            kind: "com.mygame.game-status",
            provider: GameStatusProvider(),
            placeholder: GameStatusPlaceholderView()
        ) { entry in
            GameStatusView(entry.gameStatus)
        }
        .configurationDisplayName("Game Status")
        .description("Shows an overview of your game status")
        .supportedFamilies([.systemSmall, .systemMedium, .systemLarge])
    }
}
```

- `Kind`：每个小组件都有一个唯一的`kind`，一个您选择的字符串。当您使用WidgetCenter重新加载其时间线时，您使用该字符串来识别您的小组件。

- `Timeline Provider`：时间线提供者是一个确定刷新小组件的时间线的对象。提供更新您的小组件的未来日期可让系统优化刷新过程。

  

- `Placeholder`：要首次显示您的小组件，或在锁屏上显示它，您需要提供一个占位符视图，这是一个没有特定内容的通用视觉表示。占位符视图类似于 watchOS 中复杂功能的占位符资产，只不过它是作为 SwiftUI 视图提供的。

- 内容闭包包含WidgetKit渲染小部件所需的SwiftUI视图。当WidgetKit调用内容闭包时，它会传递一个由widget提供者的snapshot(with:completion:)或timeline(with:completion:)方法创建的时间线条目。
  修改器让你指定你的widget支持的规格，以及当用户添加或编辑他们的widget时显示的细节。

## Topics

### 创建一个小部件配置

- `init<Provider, PlaceholderContent>(kind: String, provider: Provider, placeholder: PlaceholderContent, content: (Provider.Entry) -> Content)`
  - 为小组件创建一个配置，没有用户可配置的选项。
- 当Content符合View、Provider符合TimelineProvider和PlaceholderContent符合View时可用。
  
- `var body: BridgedBody`
  - 声明此小组件的内容和行为。
- `typealias Body`
  - 表示此配置主体的小组件配置类型。
  - 当内容符合View时可用。
- `typealias WidgetBody`
  - 代表此小组件主体的小组件类型。
  - 当内容符合View时可用。

### 设置显示名称「参照WidgetConfiguration的配置」

### 设置描述「参照WidgetConfiguration的配置」

### 设置支持的大小规格「参照WidgetConfiguration的配置」

### 处理后台网络请求

- `func onBackgroundURLSessionEvents(matching: ((String) -> Bool)?, ((String, () -> ()) -> ())) -> some WidgetConfiguration`
  - 添加了一个动作，当与由闭包识别的URL会话相关的事件正在等待处理时执行。

- `func onBackgroundURLSessionEvents(matching: String, ((String, () -> ()) -> ()) -> some WidgetConfiguration`
  - 添加一个动作，当与具有匹配标识符的URL会话相关的事件正在等待处理时执行。	

## 关联

### 符合于

- [`WidgetConfiguration`](Link TODO)