---
title: Weekly Dev Log 2026-W17
published: False
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W17
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202608_WeekDevLog-2026-W17/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- 2週間ぶりの更新です。先々週から長いお休みを取り、家族で夏を満喫しました。
- 夏のイベントを楽しむのに、忙しく、2週間であまり進捗はできなかったが、iOSアプリ開発については、少し進捗できた。
- 前回までは、ギター指板1音ずつの音名について答えるような内容であったが、フレット間にある出題音全てを回答するような内容に改善することをこのお休み中に行った。
- 今回の改修により、Note Practice modeの開発が概ね完了した。ここまででやっと1メニュー分の開発を終えることができた。
- 今回の改修の中で、SwiftUIプログラム処理内容などについても新たな学びを得ることができた。

---

## 📱 iOS (SwiftUI)

- Added progress tracking to show how many matching note positions have been found within the currently visible fret range.
- Used a `Set<FretPosition>` to preserve multiple correct positions and prevent the same position from being counted twice.
- Introduced a `FeedbackState` enum to manage idle, correct-answer, and wrong-answer states clearly.
- Implemented temporary answer feedback using a cancellable Swift concurrency `Task`.
- Added separate interaction controls for fret answers and fret-range navigation so each control can be disabled independently.
- Reviewed the Codex-generated SwiftUI implementation against the official Apple and Swift documentation to understand how its state management, asynchronous tasks, cancellation, and view lifecycle behavior work.
- Added a progress indicator such as `Find E 2 / 4`, showing both the number of positions already found and the total number of correct positions in the visible fret range.
- Replaced the previous single-selection state with a `Set<FretPosition>`, allowing the app to preserve multiple correct positions without storing duplicates.
- Introduced `FeedbackState` to represent the idle, correct-feedback, and wrong-feedback states clearly and safely.Added temporary `Correct!` and `Try Again` feedback that disappears after approximately one second while keeping previously found positions highlighted.
- Implemented cancellable feedback handling with Swift concurrency and UUID-based token validation, while separately controlling answer interactions and fret-range controls.
- Used Xcode breakpoints to pause `scheduleFeedbackReset()` at key points, including UUID generation, Task creation, `Task.sleep`, token validation, and the final state reset.
- Verified how the Task waits for approximately one second, validates its cancellation and token state, and then clears only the temporary answer and feedback state.

### 🎸 Note Practice modeの変更イメージ

Note Practice modeの画面で何を変更したか具体的に記します。

今回の変更では、単に出題された音名の位置を1つ当てるだけではなく、表示されているフレット範囲の中から同じ音名の位置をすべて探してもらう練習へ変更しました。

旧バージョンでは、正しい位置を1つ見つければその音についての回答は終わっていました。そのため、ユーザーが指板上の特定の位置だけを覚えていても回答できます。

新しいバージョンでは、同じ音が他の弦のどこに存在するのかも探す必要があります。これによって、音名と1つの位置を結びつけて覚えるのではなく、指板上に同じ音がどのように配置されているのかを意識しながら練習できるようにすることを狙いました。

さらに、正解するたびに進捗を表示し、すべての位置を見つけると Congratulations! を表示して次の問題へ進むようにしました。これによって、「あと何個見つければこの問題をクリアできるのか」が分かるようにしました。

#### 古いバージョン

- 7フレットの範囲で、出題音1音に対して、出題音と同じ音名位置を1つ回答する。
- 1つの回答に対して正誤判定をし、ユーザーにフィードバックする。

  _(旧バージョン:Note Practice mode)_
  ![NotePracticeMode_Old](./assets/NotePracticeMode_Old.png)

#### 新しいバージョン

- 7フレットの範囲で、出題音1音に対して、そのフレット範囲に存在する全ての出題音と同じ音名位置をユーザーに回答するように変更した。
- 1つの回答に対して正誤判定をし、ユーザーにフィードバック箇所は、同じだが、正答するごとに正答数が加算される。
- 正答数が分母の数に達するとおめでとうございます！というメッセージを出して次の問題を出題する。
- ユーザーが1つの音の位置を点として覚えるのではなく、指板上のどこに同じ音が存在するのかを探すことで、ギター指板全体の音の配置を意識してもらうことを目的に改修しました。

_(新バージョン:Note Practice mode)_
![NotePracticeMode_New](./assets/NotePracticeMode_New.jpg)

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- Modeling UI states with an enum makes SwiftUI behavior easier to understand and safer to extend than relying on multiple Boolean values.
- A `Set` is a natural choice for tracking unique answers because duplicate positions are rejected automatically.
- Cancelling the previous feedback task is not always sufficient; validating a UUID token also prevents stale asynchronous work from changing newer UI state.
- Visual state and interaction state should remain separate because a control may need to preserve its appearance while becoming temporarily disabled.
- SwiftUI’s `ButtonStyle` can affect how disabled controls are rendered, so disabled states need to be checked visually in Xcode Preview.
- I learned that an enum is safer than multiple Boolean properties for mutually exclusive UI states. An enum guarantees that the screen can only be in one valid feedback state at a time.
- I learned that adding `Equatable` to a custom enum allows its values to be compared with `==` and `!=`. For example, `feedbackState != .idle` returns `true` whenever temporary feedback is being displayed.
- I learned how a computed Boolean property can translate application state into UI behavior. `isRangeInteractionDisabled` converts the current feedback state into a value that `FretboardView` uses to enable or disable its range buttons.
- I learned that `Task<Void, Never>?` represents an optional asynchronous task that returns no result and exposes no error to its caller. Keeping the Task reference also makes it possible to cancel the current feedback timer.
- learned that Swift Task cancellation is cooperative rather than an immediate forced stop. Combining `cancel()`, `Task.isCancelled`, `Task.sleep` error handling, and UUID token comparison provides additional protection against stale state updates.
- I learned to cancel view-owned asynchronous work in `onDisappear`. This prevents a feedback Task from attempting to update the practice screen after the user has already left it.
- Learned that `.accessibilityElement(children: .combine)` groups related child views into a single accessibility element for clearer VoiceOver navigation, while `.accessibilityHidden(true)` excludes decorative icons so meaningful feedback text such as `Correct!` or `Try Again` remains the primary accessible content; this changes the accessibility structure without affecting the visual layout, but it does not automatically announce state changes or move VoiceOver focus.
- Learned that `Task.sleep` suspends the Task without blocking the underlying thread, allowing the app and MainActor to continue processing other work.
- Learned how UUID values act as generation tokens: the Task captures its own token and compares it with the latest `feedbackToken` before changing the UI state.

---

# 🚀 Next Week

- NotePracticeModeとは別の練習メニューであるChord Tone Practice modeの開発に着手する。
- Organize the UI adjustment points for the portfolio site implemented by Codex in Notion, then start making small UI refinements.
- Continue working on the AI Security Learning Path.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
