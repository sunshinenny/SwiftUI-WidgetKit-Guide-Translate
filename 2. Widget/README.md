# Widget Protocol

## Widget

在主屏幕或通知中心显示的小部件的配置和内容。

****

## 定义

```swift
protocol Widget
```

## 概述

Widget 在 iOS 的主屏幕或 macOS 的通知中心中，直接显示应用程序中一目了然的相关内容。

用户可以添加、配置和组织小部件，以满足他们的个性化需求。

你可以提供多种类型的小部件，每种小部件都能呈现特定的信息。

当用户想要获得更多信息时，比如阅读标题的完整文章或查看包裹交付的细节，小部件可以让他们快速获取应用中的信息。

Widget有三个关键组成。

- `Configuration`，它决定了小组件是否可配置，识别了小组件，并定义了显示小组件内容的SwiftUI视图。
- `Timeline Provider`「时间线提供者」，随着时间的推移更新Widget的视图。
- WidgetKit用来显示Widget的SwiftUI视图。

有关如何在应用程序中添加小部件扩展以及保持小部件最新，请分别参阅[创建小部件扩](Link TODO)和[保持小部件更新](Link TODO)。

通过添加自定义 SiriKit 意图，你可以让用户自定义他们的小组件，以显示与用户最相关的信息。

如果你已经添加了对 Siri 或快捷方式的支持，那么你就可以很好地支持可定制的小组件。如需了解更多信息，请参见[制作可配置小部件](Link TODO)。

## Topic

### 实现一个Widget

- `var body: Self.Body`
  - 小组件的内容和行为。「必须」

- `associatedtype Body : WidgetConfiguration`
  - 表示小组件内容的配置类型。「必须」
- `protocol WidgetConfiguration`
  - 描述小组件内容的类型。
- `struct EmptyWidgetConfiguration`
  - 一个空的小组件配置。

### 运行一个Widget

- `init()`
  - 以body为内容创建widget。「必须」

- `static fun main()`
  - 初始化并运行小组件。
  - 因为你在你的Widget构件的声明前加上了@main属性，系统会调用你的widget的main()方法来启动widget。SwiftUI提供了一个默认的方法实现，它以一种适合平台的方式管理启动过程。