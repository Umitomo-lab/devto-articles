---
title: Weekly Dev Log 2026-W23
published: True
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W23
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202611_WeekDevLog-2026-W23/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- The mornings have become **really chilly**, while the afternoons are still a little warmer. I can feel winter getting closer day by day. It already feels like a while ago that my kids were having fun dressing up for Halloween🎃🍂.

- Work has been getting **really busy**, so I've been thinking about how to make even a little time for the things I want to do. I haven't made as much progress as I'd hoped over the past two weeks, but I want to give myself credit for keeping at it, even when things get busy🙂.

- On the development side, I continued improving the **chord-tone practice feature** in my iOS app,**ToneDrill**🎸. I expanded the question combinations, refined the settings screen, and added more automated checks.

- The biggest new experience was **trying automated UI testing in Xcode for the first time**. I learned how a test launches the app, finds controls, waits for screens to appear, and saves screenshots for review. It reminded me that checking the app's behavior is different from only testing its underlying logic.

---

## 📱 iOS (SwiftUI)

### My first automated UI tests in Xcode 🧪

- Reviewed the existing **XCTest / XCUITest** flow for the chord-tone practice screen and learned how UI tests interact with the running app.
- Used **`XCUIApplication`** to launch the app and queries such as **`app.buttons["Start Practice"]`** to locate interface elements.
- Practiced waiting for elements, checking expected results, and performing actions such as **`tap()`**.
- Learned how to save test screenshots using **`XCTAttachment`** and inspect them in Xcode's test reports.
- Investigated an issue where screenshots had the wrong orientation. Adjusted the simulator to landscape, waited for the app window to rotate, and normalized the captured image before attaching it.
- Also explored **`performAccessibilityAudit`**. I learned that a successful audit may finish without printing a separate message to the console; the test result itself still needs to be checked.

---

# 💡 Key Takeaways

## 🧪 My First Steps with Xcode UI Testing

### How a UI test runs

- **XCTest and XCUITest:** I learned to define UI tests as methods in an **`XCTestCase`** subclass. **`setUp()`** and **`tearDown()`** can prepare and clean up the test environment before and after each test.
- **`XCUIApplication`:** Represents the app under test through a testing proxy. It provides methods to **launch, activate, and terminate** the app and query its interface.
- **`XCUIElement` and queries:** An expression such as `app.buttons["Start Practice"]` queries for a button with the specified identifier or label. The resulting element can be inspected or interacted with using methods such as **`tap()`** and **`swipeUp()`**, or properties such as **`exists`** and **`isHittable`**.

### Waiting for the screen and checking results

An interface may take time to appear after the app launches or a button is tapped. Instead of assuming that an element is already present, a test can wait for it:

```swift
XCTAssertTrue(element.waitForExistence(timeout: 5))
```

- **`waitForExistence(timeout: 5)`** waits for the element to exist, up to five seconds, and returns **`true`** if it appears or **`false`** if the timeout expires. It checks existence, **not whether the element is hittable**.
- **`XCTAssertTrue(...)`** passes when the expression evaluates to `true` and records a test failure otherwise. Combining it with `waitForExistence` makes the expected result explicit.
- **`continueAfterFailure = false`** configures the test to stop after a failure, which is useful when later interactions depend on an earlier step succeeding.

### Screenshots and accessibility checks

- **`XCTAttachment`:** Attaches screenshots or other supported data to a test activity, so the results can be reviewed later in Xcode. Setting **`attachment.lifetime = .keepAlways`** preserves the attachment even when the test passes.
- **Screenshot orientation:** Setting a simulator to landscape does not necessarily mean the captured image is immediately in the expected orientation. I learned to wait for the UI to rotate and check the orientation of the saved image.
- **`performAccessibilityAudit`:** Runs accessibility checks as part of a UI test. **No extra console message does not, by itself, prove that the audit was skipped or passed**; I need to inspect the test outcome and any reported issues.

**My takeaway:** Unit-level checks help verify question-generation rules, while **UI tests verify interactions with the running app**. I want to use both rather than treating a successful build as enough.

## 📱 Swift Learning

### Argument labels and parameter names

Swift can give a function parameter an **argument label** for the call site and a separate **parameter name** for use inside the function:

```swift
func nextQuestionCandidates(
    excluding currentSettings: ChordTonePracticeSettings
) -> [ChordTonePracticeSettings] {
    // ...
}
```

- **`excluding`** is the argument label used when calling the function, for example `nextQuestionCandidates(excluding: currentSettings)`.
- **`currentSettings`** is the parameter name used within the function body.
- The word **`excluding`** does not automatically remove anything. Actual exclusion requires logic such as **`filter`** and the condition `settings != currentSettings`.

### `filter`, `map`, and `flatMap`

- **`filter(_:)`** evaluates a predicate for each element and returns only those for which the predicate is **`true`**. For example, `settings != currentSettings` is `false` for the current question, so `filter` removes that element from the resulting collection. **The original collection is not modified.**
- **`map(_:)`** transforms each element by applying a closure and collects the results. In my app, it can turn a combination of root, quality, and pattern into a **`ChordTonePracticeSettings`** value.
- **`flatMap(_:)`**, when used with a collection-returning transformation, concatenates the resulting collections into one collection. Combined with nested loops or transformations, it can produce a **single array of all 72 question combinations**, rather than nested arrays.

### 📚 References — Apple Developer Documentation

These official references are useful when I review the APIs and concepts from this week:

- [XCTest — Apple Developer Documentation](https://developer.apple.com/documentation/xctest)
- [XCUIApplication — Apple Developer Documentation](https://developer.apple.com/documentation/xcuiautomation/xcuiapplication)
- [XCUIElement — Apple Developer Documentation](https://developer.apple.com/documentation/xcuiautomation/xcuielement)
- [XCTAttachment — Apple Developer Documentation](https://developer.apple.com/documentation/xctest/xctattachment)
- [Array — Swift Standard Library](https://developer.apple.com/documentation/swift/array)

---

# 🚀 Next Week

- Start designing the **overall structure of a new quiz-style practice mode**, so the exercises feel more like a game. I'll begin with the main features and flow before implementing the details.
- Organize the UI adjustment points for the portfolio site built with Codex in Notion, then start making small UI refinements.
- Continue working on the **AI Security Learning Path**.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
