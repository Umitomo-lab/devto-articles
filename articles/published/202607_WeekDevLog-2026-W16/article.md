---
title: Weekly Dev Log 2026-W16
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W16
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202607_WeekDevLog-2026-W16/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- This week, I was able to **make a little more progress** on my personal **iOS development project**, continuing from last week❤️‍🔥.
- By last week, I had finished implementing the main screen that is opened from the top menu. Based on that screen, I discussed **the game logic** for the single-note practice menu on the fretboard with **Codex**.
- I **enjoyed the process** of **starting with a rough idea** and gradually **turning it into** a more concrete **implementation plan**🦾.
- For the first time, I asked **Codex** to **implement unit tests** for my SwiftUI project. As a result, I noticed that **the implementation style** was **different from** the testing approach I had **learned in Apple’s SwiftUI tutorials**🤔.
- After looking into it, I found that **Codex** had used the older **XCTest** framework, so I revised the tests to use Swift **Testing**, which is easier for me to understand based on what I have learned so far.
- By accumulating discoveries like this, I want to **keep improving my ability** to develop iOS apps smoothly with AI agents🚶.
- I was also able to **continue working on TryHackMe** again this week. I only completed a small part, but I want to **keep moving forward one small step** at a time✨.

---

## 📱 iOS (SwiftUI)

- Defined the new completion logic for the current Note Practice mode through discussions with Codex.
- Finalized the progress display, feedback timers, fret-range controls, and automatic transition to the next question.
- Created the Note Practice completion feature specification and implementation plan, then updated the Task Index to reflect the latest decisions.
- Planned the SwiftUI state management, testing strategy, and file-level changes before starting implementation.
- Added completion-specific color assets for the new Note Practice feedback state.
- Implemented `NotePracticeCalculator` to calculate visible positions, target positions, and eligible note names.
- Added logic that excludes the current note when alternative questions are available.
- When I asked Codex to implement unit tests without specifying a framework, it initially used XCTest.
- Since I had learned unit testing with Swift Testing in Apple’s Swift tutorials, I decided to use Testing instead.
- Refactored the tests with `@Suite`, `@Test`, and `#expect`, adding clear Japanese display names for readability.
- Updated `AGENTS.md` to preserve the testing policy and current progress for future Codex sessions.
- Ran the `NotePracticeCalculator` unit tests in Xcode and confirmed that all tests passed.
- Investigated a Swift Concurrency warning related to the `Hashable` conformance of `FretPosition`.
- Marked `FretPosition` as `nonisolated` after confirming that it is an immutable value type with no UI dependencies.
- Added shared layout metrics for the Answer and Feedback panels to keep the UI dimensions consistent.
- Introduced `FretCellVisualState` to explicitly represent the `normal`, `found`, and `wrong` states.
- Updated `FretCellView`, its previews, and `FretboardView` incrementally while documenting the next verification steps for Xcode.

---

## 🔐 Security (TryHackMe)

- Worked on the AI System Reconnaissance room, part of the AI Security Learning Path on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- I really enjoyed brainstorming the Note Practice changes with Codex. I started with rough feature ideas and gradually saw them turn into a well-structured SwiftUI specification.
- Discussing the behavior step by step made the design process feel much more efficient.
- Separating persistent progress from temporary feedback makes SwiftUI state management clearer and safer.
- Planning interaction states, disabled appearances, tests, and accessibility before coding can prevent many implementation problems later.
- A range such as `0...6` is a `ClosedRange<Int>` that includes both endpoints.
- `map` transforms each element, while `filter` keeps the original elements that satisfy a Boolean condition.
- `Set` removes duplicates, `contains` checks membership, and `Hashable` makes custom values usable in a set.
- Codex may choose APIs or implementation styles that differ from those taught in Apple’s latest Swift and SwiftUI tutorials. These approaches are not necessarily wrong, but some may follow older conventions.
- Defining preferred modern patterns in `AGENTS.md` is important for keeping future implementations consistent and preventing the same outdated approach from being chosen again.
- I learned that Xcode’s Default Actor Isolation can implicitly isolate a type and its protocol conformances to `MainActor`.
- I learned that a `MainActor`-isolated `Hashable` conformance cannot safely be used by a nonisolated generic collection such as `Set`.
- I learned that adding `@MainActor` to a test function does not solve a warning caused by the isolation of the model type or its protocol conformance.
- I learned that `nonisolated` should be applied based on a type’s responsibilities, not added mechanically just to remove a compiler warning.

---

## 🔐 TryHackMe Learning

### AI System Reconnaissance

#### Task 4: Enumerating AI Systems

- I learned that MLflow is a highly valuable service to enumerate because it can expose experiments, registered models, model versions, training runs, and downloadable artifacts through a small number of REST API calls.
- I learned that the `model-versions/search` endpoint is especially important because it can reveal the artifact URI, user ID, timestamps, and stage labels, which show where model files are stored and whether a model is used in production or staging.
- I understood that inference servers such as Triton and TensorFlow Serving expose model metadata, including input tensor names, shapes, data types, backend frameworks, and maximum batch sizes, which can show exactly how to format a valid inference request.
- I learned that vector databases such as Qdrant, Weaviate, and Chroma can reveal what kind of data an AI system is indexing, including collection names, vector dimensions, distance metrics, point counts, schemas, and embedding model information.
- I learned how to use `curl -s` to retrieve API responses quietly without extra progress output, and how to use `jq -r` to extract specific values from JSON responses in a clean, readable format.
- I learned that Jupyter notebooks can become a serious security risk because data scientists may accidentally store cleartext credentials, access keys, or tokens in notebook cells, which can become a bridge to MLflow, cloud storage, and other parts of the AI stack.

---

# 🚀 Next Week

- Continue developing the Note Practice menu for ToneDrill.
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
