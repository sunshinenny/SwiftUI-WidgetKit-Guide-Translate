# WidgetFamily Enumeration

# WidgetFamily

小组件使用的规格：small、medium或large。

****

## 定义

```swift
enum WidgetFamily
```

## 概述

小组件可以支持一个或多个尺寸，让用户可以灵活地按照自己的喜好配置小组件。每种小组件尺寸都提供不同的细节空间，因此要考虑哪种尺寸最适合小组件显示的信息类型。有关设计小组件的更多信息，请参阅人机界面指南。

> #### Note
>
> 小组件的大小可能会在不同的设备上有所不同。您的小组件内容应该是灵活的，并避免使用固定值。

您在定义小组件的配置时，使用 supportedFamilies(_:)属性修饰符指定小组件支持的尺寸。

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

当WidgetKit向小组件的Provider询问时间线条目时，它会提供一个包含Family属性的TimelineProviderContext。这个属性告诉提供者用户选择的具体尺寸，并让你据此配置小组件的视图。

例如，在一个显示角色细节的小组件中，小尺寸可能只显示角色的头像和健康水平，而中等尺寸将包括完整的角色名称和联盟，大尺寸将包括扩展细节。

## Topics

### 创建一个 Widget Family

- `init?(rawValue: Int)`
  - 用指定的原始值创建一个新的实例。
- `var rawValue: Int`
  - 原始类型的对应值。
- `typealias RawValue`
  - 原始类型，可以用来表示所有符合类型的值。

### 访问 Widget Families

- `case systemSmall`
  - 小型Widget

- `case systemMedium`
  - 中等大小Widget

- `case systemLarge`
  - 大型Widget

### 描述 Widget Families

- `var hashValue: Int`
- `func hash(into: inout Hasher)`
  - 当Self符合Hashable且Self.RawValue符合Hashable时可用。
- `var description: String`
  - 本实例的文字表述。
- `var debugDescription: String`
  - 本实例的文字表述，适合调试。

### 比较 Widget Families

`static func != (WidgetFamily, WidgetFamily) -> Bool`

## 关联

### 符合于

- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- RawRepresentable