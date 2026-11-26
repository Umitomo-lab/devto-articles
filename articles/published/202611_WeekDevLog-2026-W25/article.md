---
title: Weekly Dev Log 2026-W25
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W25
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202611_WeekDevLog-2026-W25/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- I started using a **paper planner for the first time in years** 📓. Since I began posting these weekly Dev.to logs, I've also developed a habit of recording what I work on. That habit has helped me notice things I might otherwise have overlooked.

- Writing things down by hand has been surprisingly refreshing. It helps me **organize my thoughts and come up with new ideas**. I'd love to write a separate article about what I've discovered through journaling someday 🙂.

- On the development side, I continued planning a **game-style note quiz** for my iOS music practice app, **ToneDrill** 🎸. This week, I focused on defining how questions and difficulty levels should work, rather than jumping straight into implementation.

- I worked with **Codex** to explore game mechanics and edge cases, then used **Figma** to review the difficulty-selection screen. I learned that a design can look good on its own but still feel inconsistent with the rest of an app 🎮.

---

## 📱 iOS (SwiftUI)

### Refining the note quiz rules with Codex 🎮

- Worked with **Codex** to define the basic game flow, focusing on keeping the gameplay simple and intuitive.
- Refined the question-selection rules to provide a **greater variety of questions** rather than repeatedly asking similar ones.
- Designed different difficulty levels to make the game accessible to beginners while offering a more challenging experience for advanced players.
- Proposed an additional game mechanic to encourage players to find notes in different positions on the guitar fretboard instead of relying on familiar ones. I then worked with Codex to refine the rules and ensure that the game would remain playable in all situations.
- Organized these decisions into a **clear game specification** before moving on to UI design and implementation.

### Reviewing the difficulty-selection screen in Figma 🎨

- Created and reviewed an initial UI design for selecting the game's difficulty level.
- Compared the new design with an existing screen to check whether it was consistent with the rest of the app.
- Refined the visual feedback for the selected difficulty level to follow the app's **existing design patterns**.

**My progress this week:** The game is really starting to take shape! 🎮

---

# 💡 Key Takeaways

## 📱 Designing Game Rules with Codex

### Turning my own ideas into game rules

While discussing the game rules with **Codex**, I came up with an idea to make the game more engaging and effective as a practice tool.

I wanted to encourage players to find notes in different positions on the guitar fretboard rather than relying on familiar ones.

However, introducing a new game mechanic can affect other existing rules. For example, restricting previously used positions could eventually leave players with no valid answer.

By working through these rules with Codex, I was able to identify potential **edge cases**, separate the responsibilities of each rule, and refine my idea without breaking the overall game flow.

**My takeaway:** I don't have to simply accept what Codex initially suggests. I can contribute my own ideas and use Codex as a partner to explore how to turn them into practical, well-defined game rules.

### Clarifying game behavior before writing code

Working with Codex to explore different ideas and discuss the potential consequences of each decision helped me clarify how I wanted the game to work.

Instead of jumping straight into implementation, I focused on defining **what the game should do** before deciding **how to implement it in Swift**.

**My takeaway:** Defining the expected behavior before writing code makes it easier to identify potential problems, evaluate alternatives, and establish a clear foundation for implementation and testing.

## 🎨 Keeping New UI Consistent with the Existing App

### Review the whole product, not just one screen

While reviewing a UI design proposed by Codex, I noticed that although the design looked good on its own, it didn't fully match the visual patterns already established in my app.

This made me realize the importance of reviewing new designs in the context of the **entire application**, rather than evaluating each screen individually.

Existing screens are valuable references for maintaining consistency in appearance, interaction, and visual feedback.

**My takeaway:** Codex can help me create and refine UI designs, but it may not always take the entire product's design language into account. Human review is still important for maintaining a consistent user experience across the app.

---

# 🚀 Next Week

- Finalize the quiz's **Playing and Result screens** in Figma, then explore **motion prototypes** for Start, Resume, Time Up, and Reduce Motion behavior before implementation.
- Organize the UI adjustments for my portfolio site in Notion, then continue making small refinements.
- Continue working on the **AI Security Learning Path**.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
