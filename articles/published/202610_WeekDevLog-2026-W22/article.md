---
title: Weekly Dev Log 2026-W22
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W22
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202610_WeekDevLog-2026-W22/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Summers in Japan have been getting extremely hot in recent years. Maybe because the weather is more comfortable now, I've noticed that festivals and fireworks displays—events I usually associate with summer—are being held around this time of year instead. I've been enjoying a little bit of summer, just later than usual🎆🍂.

- On the development side, I made steady progress on **Chord Tone Practice** in my iOS app, **ToneDrill**🎸. I implemented and reviewed the settings overlay, improved the layout for larger text and VoiceOver, and added feedback for partial and completed answers.

- I spent time understanding the SwiftUI code behind these features, especially **state management, adaptive layouts, closures, and `Set` operations**. Rather than just checking whether the app builds, I also reviewed Xcode Previews and tested accessibility behavior on my iPhone.

- It's been **two weeks since my last post**, but I want to keep sharing my progress, even if it's only a little at a time🙂.

---

## 📱 iOS (SwiftUI)

- Reviewed the app's colors and visual design to make sure the screens were consistent.
- Implemented and refined the **Chord Tone Practice settings screen**, allowing users to configure their practice options. Checked the layout in different states and with larger text sizes.
- Improved **accessibility and screen layouts**, including clearer VoiceOver labels and adjustments to prevent text from being cut off. Tested the changes on my iPhone.
- Improved **answer selection and validation**, making sure users can select, remove, and replace notes correctly. Added feedback for partial answers, incorrect selections, and completed answers without losing previous valid selections.
- Adjusted the answer feedback display to match the Figma design and verified the changes through Xcode Previews, builds, and automated tests.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Adaptive layouts and text sizing

- **`ViewThatFits`** evaluates child views in the order provided and selects the first whose ideal size fits the available space along the specified axes. It can switch between layouts as available space changes; the choice is **not based on a fixed Dynamic Type threshold**.
- **`fixedSize(horizontal:vertical:)`** makes a view use its ideal size along the specified axes; it does **not** specify a numerical width or height. In an `HStack`, it can help prevent horizontal text compression. By contrast, **`.minimumScaleFactor`** lets text shrink when necessary.
- **`.dynamicTypeSize(...DynamicTypeSize.large)`** limits the maximum Dynamic Type size within the modified view to `.large`. Smaller user-selected sizes still apply, while larger ones are capped.
- **`@Environment(\.dynamicTypeSize)`** reads the current Dynamic Type size from the environment, making it possible to adapt layouts to different text sizes.
- **`.layoutPriority(1)`** gives a view higher priority when its parent distributes limited space. It can help a view resist shrinking, but **does not set a fixed width**.

### State management and settings controls

- **`@State` and `@Binding`:** `@State` stores data owned by a view, while `@Binding` allows another view to read and modify that data. Changes made through the binding update the original state. The owning view can decide whether to apply or discard draft changes. Computed values can be derived from state instead of being stored separately.
- **`LazyVGrid` and `GridItem`:** `LazyVGrid` arranges child views into columns and adds rows as needed. `GridItem` defines each column's size, spacing, and alignment.
- **`Array(repeating:count:)`** creates an array containing a value repeated a specified number of times. It can define matching grid columns, while **`ForEach`** generates the individual views. **`ForEach(..., id: \.self)`** uses each element as its identifier when the values are unique and `Hashable`.
- **Enum raw values:** `.rawValue` accesses a predefined raw value of an enum case. An app can display that value as text while using the enum case itself for program logic.

### Closures and Swift collection operations

- **Closures and `@escaping`:** A closure is a value containing executable code. **`@escaping`** allows a closure parameter to be stored or called after the receiving function returns. For example, a button can receive an action closure and execute it when tapped. Neither `@escaping` nor trailing-closure syntax executes the action immediately or makes it asynchronous.
- **Closure syntax:** The **`in`** keyword separates a closure's parameter declaration from its body. Swift can infer parameter and return types from context, and a single-expression closure can return its result implicitly.
- **`filter(_:)`** evaluates a predicate closure for each element and returns a collection containing only those for which the predicate returns `true`. It does **not** modify the original collection.
- **`Set` and `isSubset(of:)`:** A `Set` stores unique, unordered values whose element type conforms to `Hashable`. **`isSubset(of:)`** returns `true` when every element of one set exists in another. Equal sets also satisfy this condition, so it can help check partial and complete matches. Checking for an **exact match** requires an additional condition such as set equality.

### Previews, accessibility, and validation

- **Xcode Previews** make it possible to inspect a SwiftUI view in different states and text sizes. A preview-only parent view can supply the bindings and callbacks needed to test these variations.
- **Accessibility modifiers:** **`.allowsHitTesting(false)`** prevents a view from participating in hit testing. The **`.isHeader`** accessibility trait identifies a heading to assistive technologies without changing its visual appearance. Custom controls should provide meaningful accessibility labels, values, and state information.
- **Testing on a real device matters:** A successful build shows that the code compiles, not that the layout or VoiceOver interactions work as intended. Previews help inspect the design, while testing on an iPhone helps check actual accessibility behavior. App icons, code signing, and installation are separate concerns.

### 📚 References — Apple Developer Documentation

The following official documentation pages are useful for reviewing the Swift and SwiftUI features discussed above:

- [ViewThatFits — SwiftUI](https://developer.apple.com/documentation/swiftui/viewthatfits)
- [dynamicTypeSize(\_:) — SwiftUI](https://developer.apple.com/documentation/swiftui/view/dynamictypesize%28_%3A%29-26aj0)
- [layoutPriority(\_:) — SwiftUI](https://developer.apple.com/documentation/swiftui/view/layoutpriority%28_%3A%29)
- [Set — Swift Standard Library](https://developer.apple.com/documentation/swift/set)

---

# 🚀 Next Week

- Improve the **Chord Tone Practice** feature by adding more question variations, refining the settings screen, and strengthening automated tests.
- Organize the UI adjustment points for the portfolio site implemented by Codex in Notion, then start making small UI refinements.
- Continue working on the **AI Security Learning Path**.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
