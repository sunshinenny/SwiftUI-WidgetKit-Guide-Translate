# WidgetBundle Protocol

# WidgetBundle

用于从单个widget扩展中显示多个widget的容器。

****

## 定义

```swift
protocol WidgetBundle
```

## 概述

要支持多种类型的widget，请在符合WidgetBundle的结构中添加@main属性。例如，一个游戏可能有一个小组件来显示游戏的摘要信息，而另一个小组件则显示单个角色的详细信息。body 属性使用 @WidgetBundleBuilder 属性将两个小组件分组。

```swift
@main
struct GameWidgets: WidgetBundle {
   @WidgetBundleBuilder
   var body: some Widget {
       GameStatusWidget()
       CharacterDetailWidget()
   }
}
```



## Topic

### 实现 Widget Bundle

- `var body: Self.Body`
  - 声明应用程序支持的小部件组。「必须」

- `associatedtype Body : Widget`
  - 表示捆绑内容的小部件类型。「必须」
- `protocol WidgetConfiguration`
  - 描述小组件内容的类型。
- `struct WidgetBundleBuilder`
  - 自定义属性，用于构造widget bundle的主体。

### 运行 Widget Bundle

- `init()`
  - 使用bundle的主体作为其内容创建一个widget bundle。「必须」

- `static fun main()`
  - 初始化并运行widget bundle。