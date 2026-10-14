---
title: Weekly Dev Log 2026-W21
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W21
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202610_WeekDevLog-2026-W21/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- The weather has finally become more comfortable here in Japan, and I've been feeling excited to get outside🍂. Recently, I took a spontaneous day trip to a small island and enjoyed the beautiful scenery filled with cosmos and other autumn flowers🌸.

- On the development side, I finished reviewing the tests for **Chord Tone Practice** and followed the backend calculations step by step🎸. I also learned more about Swift's collection operations and how bitmasks can generate subsets.

- I completed the **AI System Reconnaissance** room on TryHackMe🔐, learning how to approach AI reconnaissance systematically and recognize signs of this activity in logs.

- Overall, it was a week of **reviewing, understanding, and building confidence** in what I've already implemented.

---

## 📱 iOS (SwiftUI)

- Completed a detailed review of every test in `ChordTonePracticeCalculatorTests.swift`.
- Traced each test case into `ChordTonePracticeCalculator` and the related model types to understand the full calculation flow.
- Verified how chord tones, interval labels, valid answer sets, and invalid submissions are calculated.
- Reviewed the exhaustive test covering all **504 combinations** of root notes, chord qualities, patterns, and visible fret ranges.
- Examined how the tests verify pattern availability, overlapping answer sets, reachable combinations, and fret-range transitions.
- Reviewed how Swift Testing uses `@Suite`, `@Test`, `#expect`, and `#require` to organize tests and validate behavior.
- Reviewed Swift collection operations and condition-checking APIs used throughout the implementation.
- Learned how subset generation with bitmasks works.

---

## 🔐 Security (TryHackMe)

- Completed **Task 6: Structured Reconnaissance Methodology and Detection**.
- Completed the **AI System Reconnaissance** room in the AI Security Learning Path.
- Reviewed how reconnaissance can be organized into repeatable phases and how AI-specific reconnaissance activity can be detected through logs and monitoring data.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Understanding `answerSets()`

- `answerSets()` uses `compactMap` to convert each chord degree into a note name while removing any failed conversions. For example, C major with degrees `1-3-5` produces `["C", "E", "G"]`.

- A `guard` statement compares the number of converted notes with the original number of degrees. If `compactMap` removed any failed conversion, the counts no longer match and the function returns `[]`.

- For each consecutive string group, `zip` pairs the selected strings with the target notes. For example, `[5, 4, 3]` paired with `["C", "E", "G"]` becomes `(5, C)`, `(4, E)`, and `(3, G)`.

- `positions()` finds the corresponding `GuitarString`, searches the seven visible frets, and returns only the fret positions that match the target note.

- If any target string has no matching fret position, `contains(where: \.isEmpty)` rejects that string group.

- When every string has at least one matching position, `cartesianProduct()` generates every valid combination. It uses `reduce` to repeatedly extend the combinations, while `map` creates the next set of partial combinations and `flatMap` merges the nested results into `[[FretPosition]]`.

- Returning `[]` from the `flatMap` closure removes only the result for the current string group because an empty array contributes no elements to the flattened result.

### Swift collection operations and conditions

- `map` transforms every element in a collection.

- `compactMap` transforms elements and removes any `nil` results.

- `flatMap` transforms elements and flattens the nested results into a single collection.

- `filter` keeps only elements that satisfy a predicate.

- `first(where:)` searches from the beginning and returns the first matching element, or `nil` when no match exists.

- `contains`, `contains(where:)`, and `allSatisfy` express different kinds of conditions: whether a collection contains a particular value, whether **any** element satisfies a predicate, or whether **every** element satisfies one. `allSatisfy` also returns `true` for an empty sequence.

- `sorted(by: >)` returns a new array in descending order because the comparison closure says that a larger value should appear before a smaller one. It does not modify the original array.

- `Set(positions.map(\.stringNumber))` removes duplicate string numbers. Comparing the resulting count with `3` verifies that three different strings were selected.

### Iteration, testing, and debugging

- I reviewed every test in `ChordTonePracticeCalculatorTests.swift`, following each test into `ChordTonePracticeCalculator` and its related models to understand how chord tones, interval labels, valid answer sets, and invalid submissions are calculated.

- The exhaustive test covers **504 combinations** of root notes, chord qualities, patterns, and visible fret ranges. I examined how the tests check pattern availability, overlapping answer sets, reachable combinations, and fret-range transitions.

- Swift Testing uses `@Suite` to group tests, `@Test` to identify test functions, and `#expect` and `#require` to check test conditions. Unlike a failed `#expect`, a failed `#require` stops the current test's execution by throwing an error.

- `enumerated()` pairs each collection element with a zero-based offset.

- Writing `(index, submission)` in a `for` loop destructures the tuple returned by `enumerated()` into the counter and the original element.

- `#expect` is evaluated each time the loop reaches it. A failed expectation is recorded by Swift Testing, but it does not automatically stop the remaining loop iterations.

- Storing a function result in a local variable before passing it to `#expect` makes debugging easier because the input and the calculated result can be inspected separately in Xcode.

- LLDB commands such as `v value` and `po type(of: value)` are useful for inspecting runtime values and types. When evaluating closure expressions in LLDB, entering the expression on one line can make the command easier to execute.

- `allCases` lists every case of a `CaseIterable` enum, `indices` provides the valid indices of a collection, and `enumerated()` provides offset-and-element pairs.

- Swift features such as `guard`, the ternary operator (`condition ? a : b`), nil-coalescing (`??`), compound assignment (`+=`), key paths such as `\.count`, and method references such as `candidateSubset.contains` can make conditions and transformations more concise.

### Generating subsets with bitmasks

- A set containing `n` elements has `2ⁿ` possible subsets, including the empty subset and the full set.

- Each integer from `0` through `2ⁿ - 1` can represent one subset as a binary bitmask.

- `1 << index` creates a value with the bit at `index` turned on.

- `mask & (1 << index)` checks whether that bit is present in the current mask. If the result is non-zero, the element at that index belongs to the current subset.

---

## 🔐 TryHackMe Learning

- AI reconnaissance can be organized into a repeatable five-phase methodology: **passive reconnaissance, active scanning, API fingerprinting, metadata extraction, and supply chain review**.

- Passive reconnaissance can reveal information about AI infrastructure without directly touching the target network. Sources can include Shodan, Censys, FOFA, GitHub searches, arXiv papers, engineering blogs, public container registries, and job postings.

- Active scanning should consider AI-specific services and ports in addition to traditional web services. Services such as gRPC APIs and Prometheus metrics endpoints may require follow-up checks with tools such as `grpcurl` and `curl`.

- API fingerprinting examines AI-specific endpoints, response headers, JSON structures, and error messages to identify frameworks and services exposed behind HTTP interfaces.

- Metadata extraction from confirmed AI services can reveal information such as MLflow experiments, registered models, artifact URIs, user IDs, Triton model tensor specifications, vector database schemas, and Jupyter notebook credentials.

- Reconnaissance activity can also leave identifiable traces in SIEM and monitoring logs, including AI-aware port scans, scripted MLflow API access without normal UI sessions, Prometheus scraping from unknown IP addresses, Jupyter API access without session cookies, and repeated model-enumeration requests.

- Reducing the reconnaissance surface includes practical controls such as enabling MLflow authentication, restricting Jupyter access, blocking unnecessary AI-specific ports, limiting access to Prometheus metrics, rotating and scoping Hugging Face tokens, and auditing MinIO or S3 bucket policies used for model artifacts.

---

# 🚀 Next Week

- Start implementing the **Chord Tone Practice UI** step by step.
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
