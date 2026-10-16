---
title: Weekly Dev Log 2026-W21
published: True
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

- Completed a detailed review of `ChordTonePracticeCalculatorTests.swift`, the test file for my **Chord Tone Practice** feature, which helps users practice locating chord tones on a guitar fretboard.
- Traced the tests into `ChordTonePracticeCalculator`, the app's chord-tone calculation component, and its related models to understand how notes, interval labels, valid answer sets, and invalid submissions are handled.
- Reviewed an exhaustive test covering **504 combinations** of root notes, chord qualities, patterns, and visible fret ranges, including checks for pattern availability, overlapping answers, reachable combinations, and fret-range transitions.
- Studied Swift's standard collection APIs, condition checking, bitwise operations, and Swift Testing while reviewing the implementation.

---

## 🔐 Security (TryHackMe)

- Completed **Task 6: Structured Reconnaissance Methodology and Detection**.
- Completed the **AI System Reconnaissance** room in the AI Security Learning Path.
- Reviewed how reconnaissance can be organized into repeatable phases and how AI-specific reconnaissance activity can be detected through logs and monitoring data.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Collection transformations and combinations

- `map` applies a transformation to each element and returns the transformed results. `compactMap` also removes `nil` results, producing a collection of non-optional values.
- `flatMap` applies a transformation that returns a sequence for each element, then concatenates those sequences into a single collection. If a transformation returns an empty array, that element contributes no values to the result.
- `filter` keeps elements that satisfy a predicate, while `first(where:)` returns the first matching element as an optional value, or `nil` if none matches.
- `zip` pairs the elements of two sequences in order and stops when the shorter sequence ends. For example, combining `[5, 4, 3]` and `["C", "E", "G"]` produces `(5, "C")`, `(4, "E")`, and `(3, "G")`.
- `reduce` combines the elements of a sequence into one accumulated result using an initial value and a closure. It can also be used with `map` and `flatMap` to build combinations incrementally: extend each existing partial combination with each possible next element, then flatten the results.
- `Set(values.map(\.id))` is one way to collect unique identifiers from a sequence, provided the identifiers conform to `Hashable`. Comparing the resulting count with the expected number can check whether the identifiers are distinct.

### Conditions, ordering, and Swift syntax

- `contains(_:)` checks whether a sequence contains an equal value; `contains(where:)` checks whether **at least one** element satisfies a predicate; `allSatisfy(_:)` checks whether **every** element does. `allSatisfy` returns `true` for an empty sequence.
- A key-path expression such as `\.isEmpty` can be passed as a predicate when its type fits the method's requirements. For example, `groups.contains(where: \.isEmpty)` returns `true` if any inner collection is empty.
- `sorted(by: >)` returns a new collection in descending order by specifying that larger values should come first. Unlike `sort(by:)`, it does not reorder the original array.
- `guard` requires a condition to hold before execution continues; its `else` branch must transfer control out of the enclosing scope. It can help detect unexpected results, such as when `compactMap` produces fewer elements than the original collection.
- The ternary operator (`condition ? a : b`), nil-coalescing operator (`??`), and compound assignment (`+=`) express conditional values, fallbacks, and updates concisely. A method reference such as `allowedValues.contains` can also be passed where a matching closure is expected.

### Iteration, Swift Testing, and debugging

- `CaseIterable` provides `allCases` for types that support enumerating their cases; `indices` provides a collection's valid indices; and `enumerated()` pairs elements with zero-based offsets. These offsets are not guaranteed to be the same as the collection's indices.
- A loop such as `for (offset, element) in values.enumerated()` destructures each pair into its offset and element.
- In Swift Testing, `@Test` marks a test function. Related tests can be grouped in a suite type; `@Suite` explicitly annotates the type and supports suite configuration, but is not required for a type containing tests to be recognized as a suite.
- `#expect` records a failed expectation and allows the test to keep executing. `#require` records a failure and throws an error, preventing the current execution path from continuing when its requirement is not met. Both can be evaluated within loops.
- Saving a calculated result in a local variable before checking it with `#expect` makes it easier to examine inputs and outputs separately during debugging.
- In LLDB, commands such as `v value` and `po type(of: value)` help inspect values and types at runtime. Writing a closure-based expression on one line can make it easier to enter in the debugger.

### Generating subsets with bitmasks

- A collection of `n` distinct elements has `2ⁿ` subsets, including the empty subset and the full set.
- Integers from `0` through `2ⁿ - 1` can represent these subsets using binary bitmasks, with one bit assigned to each element.
- `1 << index` shifts the binary value `1` left by `index` positions to select a particular bit.
- `mask & (1 << index)` performs a bitwise AND. A non-zero result means the selected bit is set, so the corresponding element belongs to that subset.

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
