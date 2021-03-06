---
title: "How to create multiple screen previews in SwiftUI"
date: 2020-04-06T12:39:36.964Z
categories:
  - little-bites
tags:
  - swift
  - xcode
  - swiftui
comments: true
---
Today I learned that you can actually create multiple Xcode screen previews in SwiftUI.

Assuming you have a SwiftUI `View` named `ContentView`. In the `PreviewProvider`, create a `Group` and init multiple `ContentView()` children inside of it. For example:

```swift
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        Group {
            ContentView()
                .previewDevice(PreviewDevice(rawValue: "iPhone 11"))
                .previewDisplayName("iPhone 11") // Optional
            ContentView()
                .previewDevice(PreviewDevice(rawValue: "iPhone 8"))
                .previewDisplayName("iPhone 8 Dark")
                .environment(\.colorScheme, .dark)
                .environment(\.sizeCategory, .accessibilityLarge)
            ContentView()
                .previewDevice(PreviewDevice(rawValue: "iPhone SE"))
                .previewDisplayName("iPhone SE")
        }

    }
}
```

This will display the `View` that you have created in 3 previews with the following order:

1. Display it in iPhone 11
2. Display it in iPhone 8 with dark mode enabled and large accessibility size font set
3. Display it in iPhone SE

Here's how the above code will look like in action

![Xcode 11 Multiple Previews](/images/uploads/preview.gif)

This is going to be super useful when you want to quickly preview your `View` in different screen sizes, accessibility mode or color schemes. Neat huh?

References:
- [Hacking With Swift - SwiftUI tips and tricks](https://www.hackingwithswift.com/quick-start/swiftui/swiftui-tips-and-tricks)