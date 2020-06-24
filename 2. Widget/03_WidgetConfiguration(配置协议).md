# Protocol(协议)

# WidgetConfiguration

描述小组件内容的类型。

| Availability 可用性 | Framework 框架 |
| ------------------- | -------------- |
| iOS 14.0+           | SwiftUI        |
| macOS 10.16+        |                |

****

## 定义

```swift
protocol WidgetConfiguration
```

## Topics

### Implementing a Widget (实现一个小组件)

- `var body: Self.Body`
  - 声明此小组件的内容和行为。「必须」
- `associatedtype Body : WidgetConfiguration`
  - 表示该配置主体的小组件配置类型。「必须」

### Instance Methods (实例方法)

- `func configurationDisplayName<S>(S) -> some WidgetConfiguration`
  - 设置用户添加或编辑小组件时显示的小组件名称。
  - 当S符合StringProtocol时可用。
- `func configurationDisplayName(Text) -> some WidgetConfiguration`
  - 设置用户添加或编辑小组件时显示的小组件名称。

- `func configurationDisplayName(LocalizedStringKey) -> some WidgetConfiguration`
  - 设置用户添加或编辑小组件时显示的本地化名称。

- `func description(Text) -> some WidgetConfiguration`
  - 设置用户添加或编辑小组件时显示的小组件描述。
- `func description<S>(S) -> some WidgetConfiguration`
  - 设置用户添加或编辑小组件时显示的小组件描述。
  - 当S符合StringProtocol时可用。
- `func description(LocalizedStringKey) -> some WidgetConfiguration`
  - 设置当用户添加或编辑小组件时为小组件显示的本地化描述。
- `func onBackgroundURLSessionEvents(matching: ((String) -> Bool)?, ((String, () -> ()) -> ())) -> some WidgetConfiguration`
  - 当与URL会话相关的事件正在等待处理时，添加一个动作来执行。

- `func onBackgroundURLSessionEvents(matching: String, ((String, () -> ()) -> ())) -> some WidgetConfiguration`
  - 当与URL会话相关的事件正在等待处理时，添加一个动作来执行。

- `func supportedFamilies([WidgetFamily]) -> some WidgetConfiguration`
  - 设置小组件支持的大小。

## 关联

### 符合标准的类型

[EmptyWidgetConfiguration](Link TODO)