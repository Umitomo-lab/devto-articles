---
title: Weekly Dev Log 2026-W24
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W24
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202611_WeekDevLog-2026-W24/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Work has been **really busy**, and finding time for my personal projects hasn't been easy. But I've managed to make a little progress by using small pockets of free time. I realized that simply **spending less time mindlessly scrolling through social media** gives me more time than I expected. It's funny how much time I can waste without even noticing 😂.

- At the same time, I think **having time to switch off and do nothing** is important too. I don't want to turn every spare minute into something productive. I'm trying to find a healthy balance so I can keep enjoying my hobbies without pushing myself too hard 🙂.

- On the development side, I started working on a **new game-style quiz mode** for my iOS music practice app, **ToneDrill**🎸. The idea is to make the note and chord-tone exercises I've already built more engaging by adding a timed challenge and a results screen.

- This week was mostly about **planning before coding**. I worked out the basic game rules with Codex, organized the implementation steps, and refined the new menu design in Figma. It was fun seeing the idea take shape even before starting the main implementation! 🎮

---

## 📱 iOS (SwiftUI)

### Starting a new game-style quiz mode 🎮

- Created a **shared specification** for two existing types of music exercises: identifying notes and practicing chord tones. The goal is to offer both as game-style quizzes from one menu.
- Organized the work into phases, from **menu design** and **game-rule planning** through implementation and final verification, and recorded the plan in the project's task files.
- Finalized the **Figma menu design** with two quiz cards, custom icons, a timer element, and accessibility-related UI states.
- Defined the initial **minimum viable product (MVP)** rules shared by both games: a **60-second timer**, a countdown, scoring, accuracy, a results screen, difficulty levels, record tracking, and handling for interruptions.

**My progress this week:** The main achievement was creating a clear starting point for the new mode. The game itself is **not finished yet**; I focused on its design and specification first.

---

# 💡 Key Takeaways

## 📱 Planning a Feature Before Implementation

### Start with the overall direction

Before writing code, I discussed the new quiz mode with **Codex** and documented the decisions in task-management files.

- A **parent specification** helps keep the two quiz types aligned around the same overall goal.
- A **phased roadmap** gives me an order for the work without requiring every implementation detail to be decided immediately.
- Starting with a small, shared set of **MVP rules** makes it easier to separate the essential game behavior from ideas that can be added later.

**My takeaway:** I don't need to settle every detail at the beginning. It's more useful to agree on the purpose, scope, and next steps, then refine the implementation as I go.

### Using Codex and Figma to refine UI designs 🎨

This week, I also learned more about how to iterate on a design while keeping related UI elements consistent.

- I could describe specific adjustments to **Codex**, make changes in **Figma**, and continue reviewing the updated design instead of starting again from scratch.
- The workflow was particularly helpful when similar changes needed to be applied consistently across the design.

**My takeaway:** Small design adjustments are easier to manage when I review them against the full screen instead of treating each element separately.

### Defining rules shared by both quiz games

Both practice modes need the same core game behavior, so I wrote down the rules before implementing them:

| Element       | Initial rule or planned behavior             |
| ------------- | -------------------------------------------- |
| Time limit    | A **60-second** challenge                    |
| Start         | A countdown before the quiz begins           |
| Performance   | Track **score** and **accuracy**             |
| Finish        | Display the results                          |
| Challenge     | Support different **difficulty levels**      |
| Progress      | Keep **records** of past results             |
| Interruptions | Define how the game behaves when interrupted |

These are **planned MVP requirements**, not features I have already completed.

**My takeaway:** Discussing the rules with Codex helped me keep the design simple and focus on a shared foundation before adding more complicated game mechanics.

---

# 🚀 Next Week

- Start working on the **Note Quiz game**, focusing on its rules, difficulty levels, and UI design.
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
