---
title: Weekly Dev Log 2026-W20
published: True
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W20
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202609_WeekDevLog-2026-W19/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- It’s been **two weeks since my last update**. I had a long break of about five days, and here in Japan, it’s really starting to feel like autumn🍂. This time of year is perfect for picnics, so it’s been nice to enjoy the cooler weather.

- I also planted some lavender seeds with my kids that we received at a local event, and they’ve just started to sprout recently🌱. It’s been fun checking on them together and watching them grow little by little.

- This week, I finally started implementing the backend logic for **Chord Tone Practice**, following the UI design work I completed in my previous update🎸.

- I worked with Codex to implement the core models, calculation logic, and tests for **Chord Tone Practice**. Since the requirements and implementation plan were already organized, the initial implementation was completed quite quickly.

- I then reviewed the backend logic using the `ChordTonePracticeCalculatorTests` created during development, checking the official Swift documentation whenever I found something I did not fully understand.

- It still takes me much longer to understand the generated code than to generate it, but that gap is gradually getting smaller as I learn more Swift.

- I also had some time to continue the **AI Security Learning Path on TryHackMe** this week🔐. I worked on the **AI System Reconnaissance** room and learned how exposed components such as model registries, Jupyter notebooks, inference servers, and other AI-related services can reveal a much larger attack surface than a single exposed service might suggest.

- Overall, this week felt less like simply adding a new feature and more like a combination of **implementation, code review, and learning**.

---

## 📱 iOS (SwiftUI)

- Implemented the core models for **Chord Tone Practice**, including chord qualities, chord-tone degrees, patterns, settings, and answer sets.
- Added the calculation logic used to generate chord tones and valid three-note answer sets across consecutive strings.
- Added Swift Testing coverage for note calculations, interval labels, answer matching, and invalid answer combinations.
- Started reviewing the backend implementation using the `ChordTonePracticeCalculatorTests` generated during development.
- Followed the test flow to understand how valid answer sets are created, normalized, and compared.
- Reviewed how `sorted(by:)` works in Swift and how comparison closures determine the order of values.
- Learned more about the different roles of `CaseIterable`, `Identifiable`, and `Hashable`.
- Reviewed how `nonisolated` can be used for value models that do not depend on `MainActor`-isolated UI state.

---

## 🔐 Security (TryHackMe)

- Continued working on the **AI System Reconnaissance** room in the AI Security Learning Path.
- Learned how separate findings can be connected to build a larger map of an AI system's attack surface.
- Reviewed how exposed services such as MLflow, Jupyter notebooks, model registries, inference servers, and monitoring systems can reveal information about other parts of an AI environment.
- Learned why model registries can be valuable reconnaissance targets because they may expose model names, versions, artifact locations, timestamps, and other metadata.
- Studied AI supply chain risks, including exposed access tokens, external model sources, and poisoned dependencies.
- Learned how reconnaissance techniques against AI systems can be mapped to **MITRE ATLAS**.
- Reviewed the ShadowRay case study and how exposure of a single AI-related component could contribute to a much larger compromise.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- Separating music-theory calculations from SwiftUI state makes the core logic easier to test and understand independently from the UI.
- Automated tests are useful not only for checking whether code works, but also as a guide for understanding unfamiliar implementation logic.
- `CaseIterable`, `Identifiable`, and `Hashable` may appear together on the same enum, but each provides a different capability.
- `CaseIterable` provides `allCases`, which is useful when iterating through every possible enum case in tests or UI controls.
- `Identifiable` provides stable identity for values used by SwiftUI components such as `ForEach`.
- `Hashable` allows values to be used in collections such as `Set` and as dictionary keys.
- A `sorted(by:)` closure does not directly move elements. Instead, it defines whether one value should appear before another.
- Normalizing values into a consistent order makes it easier to compare logically identical answer sets even when the player selects notes in a different order.
- `nonisolated` can be useful for pure value models that do not depend on actor-isolated UI state.
- Reviewing AI-generated code while referring to the official Swift documentation is helping me gradually build a better understanding of Swift itself.

## 🔐 TryHackMe Learning

- A single exposed AI-related service can reveal much more than information about that service alone.
- AI systems can have a wider attack surface because many specialized services, tools, models, and external dependencies communicate with each other.
- Reconnaissance becomes more meaningful when individual findings are connected into a larger picture of the system.
- Model registries and other AI infrastructure can reveal useful metadata about an organization's models, environments, and dependencies.
- AI reconnaissance techniques can be classified using frameworks such as MITRE ATLAS.

---

## 💬 A Question for Developers Using AI Coding Agents

There is one thing I’ve been wondering about recently.

When I use Codex, the actual implementation can sometimes be completed in just a few dozen minutes, especially after I have already organized the requirements and written an implementation plan.

However, understanding and reviewing the generated code still takes me much longer.

Since this is my first time building an app with Swift, I often go through the implementation carefully and refer to the official Swift documentation whenever I find syntax or concepts that I do not fully understand.

Honestly, it would not be an exaggeration to say that I sometimes spend **more than ten times as long reviewing and understanding the implementation as Codex spent generating it**😅.

At the same time, I’m becoming more familiar with Swift, and I can clearly feel that this review process is getting faster.

This made me curious about developers who already have a solid understanding of the programming language they are using:

**When you use an AI coding agent to implement something, how much time do you usually spend reviewing and understanding the generated code afterward?**

Do you read through almost everything carefully, or do you mainly focus on important areas such as architecture, tests, security, and edge cases?

I’d be really interested to hear how other developers approach this.

---

# 🚀 Next Week

- Continue reviewing the `ChordTonePracticeCalculatorTests` and use them to better understand the backend implementation and Swift concepts involved.
- Continue implementing **Chord Tone Practice** as I become more confident in the backend logic.
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
