# Associated Type(相关类型)

## Body

代表小组件内容的配置类型。「必须」

| Availability 可用性 | Framework 框架 |
| ------------------- | -------------- |
| iOS 14.0+           | SwiftUI        |
| macOS 10.16+        |                |

****

## 定义

```swift
associatedtype Body : WidgetConfiguration
```

## 情况

当你创建一个自定义widget时，Swift会从你对所需body属性的实现中推断出这个类型。