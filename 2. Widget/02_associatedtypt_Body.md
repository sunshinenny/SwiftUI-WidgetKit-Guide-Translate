# Instance Property(实例属性)

## body

小组件的内容和行为。「必须」

| Availability 可用性 | Framework 框架 |
| ------------------- | -------------- |
| iOS 14.0+           | SwiftUI        |
| macOS 10.16+        |                |

****

## 定义

```swift
var body: Self.Body { get }
```

## 情况

对于您创建的任何widget，提供一个计算好的body属性，将widget定义为SwiftUI视图的组成。
Swift 根据 body 属性的内容来推断小组件的 Body 关联类型。