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

- Reviewed the Xcode validation results for **color assets, design tokens, and temporary fret-cell styling**, and recorded the completed checks.
- Implemented the **Chord Tone Practice settings overlay**, including the controls for configuring practice settings. Added seven initial previews to review initial setup, reconfiguration, and larger Dynamic Type sizes.
- Walked through `ChordTonePracticeSettingsOverlay.swift` to understand **layout, `@State` / `@Binding` ownership, button callbacks, and accessibility**. Reviewed the overlay against the design, fixed a truncated Phase 4-A header, and confirmed that the four focused previews displayed correctly.
- Added a temporary app icon and tested **VoiceOver on my iPhone**. Also refined fretboard accessibility labels and the Answer layout after checking the accessibility previews, reducing unwanted text truncation and stretching.
- Verified that selecting, deselecting, and replacing chord tones worked as expected. Then implemented **partial-answer validation** to determine whether the currently selected fret positions could still form one of the remaining correct chord-tone sets.
- Added **`Good!`, single-cell incorrect-answer feedback, `Correct!`, and completion states**. An incorrect tap no longer clears previously selected temporary answers.
- Adjusted the feedback badge to match the **220 × 42** frame in Figma, and verified the implementation with a successful build and automated tests. Recorded the completed reviews in the project task documents.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Adaptive layouts and text sizing

- **`ViewThatFits`** evaluates its child views in the order provided and selects the first whose _ideal size_ fits the proposed space along the specified axes (horizontal, vertical, or both). It can switch from a horizontal layout to a vertical layout or a scrollable alternative as available space changes; the selection is **not based on a fixed Dynamic Type threshold**.
- **`fixedSize(horizontal:vertical:)`** makes a view use its ideal size along the specified axes; it does **not** assign a numerical width or height. In an `HStack`, `.fixedSize(horizontal: true, vertical: false)` can prevent a text-containing group from being compressed horizontally. By contrast, **`.minimumScaleFactor`** allows text to scale down when necessary.
- **`.dynamicTypeSize(...DynamicTypeSize.large)`** limits the _maximum_ Dynamic Type size within the modified view to `.large`. Smaller user-selected sizes still apply; larger sizes are capped in that view.
- **`@Environment(\.dynamicTypeSize)`** reads the Dynamic Type size from the current environment. I used it to select an accessibility-specific layout while allowing the Answer text to grow.
- **`.layoutPriority(1)`** raises a view's priority when its parent distributes space among children. It can help the Answer panel resist shrinking when an `HStack` becomes crowded; it **does not set a fixed width**.

### State management and settings controls

- **`@State` and `@Binding`:** The parent stores editable draft settings in `@State`; the child receives a `@Binding` to those settings through a value such as **`$draftSettings`**. Changes made through the binding update the parent's draft, while the parent decides whether to apply or discard it. A computed selection flag such as `isSelected` can be derived from the draft instead of being stored as additional state.
- **`LazyVGrid` and `GridItem`:** `LazyVGrid` lays out child views in columns, adding rows as needed. `GridItem` describes a column's size, spacing, and alignment. I used **six flexible columns** for twelve root-note buttons, forming a **6 × 2** grid.
- **`Array(repeating:count:)`** creates an array containing the specified value repeated a given number of times. It helped define the six matching `GridItem` columns; **`ForEach`** generates the individual buttons. When note strings are unique, **`ForEach(..., id: \.self)`** can use each string as its identifier.
- **Enum raw values:** `.rawValue` returns the predefined raw value of an enum case, such as `"Major"` or `"Minor"`. The UI can show that text while selection logic continues to work with the enum case itself.

### Closures and Swift collection operations

- **Closures and `@escaping`:** A closure is a value containing executable code. **`@escaping`** permits a closure parameter to be stored or invoked after the function receiving it returns. In my `optionButton` helper, an action is passed to `Button` and called when the user activates it. Neither `@escaping` nor trailing-closure syntax executes the action immediately or makes it asynchronous.
- **Closure syntax:** The **`in`** keyword separates a closure's parameter declaration from its body. Swift can infer parameter and return types from context; a single-expression closure can return its expression implicitly.
- **`filter(_:)`** evaluates a predicate closure for each element and returns a new collection containing the elements for which the predicate is `true`. It does **not** modify the original collection.
- **`Set` and `isSubset(of:)`:** A `Set` stores unique, unordered values whose element type conforms to `Hashable`. **`selected.isSubset(of: answer)`** returns `true` when _every_ selected element is contained in `answer`. Equality also counts as a subset, so the method can help check both valid partial selections and complete selections. Checking whether an answer is **fully complete** still requires an additional condition, such as set equality.

### Previews, accessibility, and validation

- **Preview helpers:** `ChordToneSettingsPreview` is a preview-only parent that supplies bindings and callbacks so the overlay can be examined in different states.
- **Accessibility modifiers:** **`.allowsHitTesting(false)`** removes a view from touch hit testing; **`.isHeader`** provides the accessibility header trait without changing the visual styling of the heading. Standard SwiftUI controls provide basic VoiceOver behavior, but custom controls need meaningful labels, values, and state information.
- **Testing on a real device matters:** A successful build confirms that the code compiles, not that the layout looks correct or VoiceOver behaves as intended. Xcode Previews help check layouts; testing on an iPhone helps verify actual accessibility interactions. An app icon is also separate from the code-signing and installation requirements.

**Apple documentation for review:** [ViewThatFits](https://developer.apple.com/documentation/swiftui/viewthatfits) · [Dynamic Type size range](https://developer.apple.com/documentation/swiftui/view/dynamictypesize%28_%3A%29-26aj0) · [layoutPriority(\_:)](https://developer.apple.com/documentation/swiftui/view/layoutpriority%28_%3A%29) · [Set and subset operations](https://developer.apple.com/documentation/swift/set)

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
