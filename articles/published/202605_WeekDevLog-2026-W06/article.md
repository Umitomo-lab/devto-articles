---
title: Weekly Dev Log 2026-W06
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W06
tags: beginners, devjournal, security, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202605_WeekDevLog-2026-W06/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Made a little more progress in the SwiftUI tutorial.
- Started the journey of building my future portfolio site. First, I created the project files and set up a repository on GitHub. I also started reserching React Router v7 by reading its documentation. I'm moving forward little by little
- Completed the ContAInment room from the AI Security Learning Path on TryHackMe this week.

---

### 💡 Thoughts on the ContAInment Room

This room was a hands-on investigation exercise set in a scenario where a company had suffered a security breach, resulting in important data being encrypted and used for blackmail. The goal was to investigate the compromised environment and discover the hidden flags🔎

I felt that this room built nicely on the concepts I learned in the previous AI Forensics room. One thing I especially enjoyed was solving the investigation by using a dedicated **AI assistant** available inside the victim environment🤖

As I worked through the challenge, I had to think carefully about what looked suspicious and follow clues step by step while actively using Linux commands. It also turned out to be **a great review of Linux operations and practical investigation workflows**🔥

---

## 📱 iOS (SwiftUI)

- Worked through the SwiftUI tutorial and completed Sections 7 and 8: "Create an Algorithm for Badges"

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to 📝
- Created a new React Router v7 project for my future portfolio site.

---

## 🔐 Security (TryHackMe)

- Completed the ContAInment room (part of the AI Security Learning Path) on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Section 8: Calculate and Show Streaks

- Learned how to calculate a daily streak by comparing saved dates with the current day.
- Understood how reversing the array helps process moments from newest to oldest.
- Learned how `map` and `compactMap` can transform `Moment` objects into simple day offsets like `[0, 1, 2]`.
- Understood how `Calendar.dateComponents` calculates date differences in calendar-based units.
- Learned that multiple moments on the same day should count as a single streak day.
- Realized that the `streak` variable represents the next expected day offset during the calculation.
- Learned that comparing `daysAgo == streak` is a simple way to detect consecutive days.
- Understood why using the end of the current day makes streak calculations more stable and predictable.
- Learned that `@ViewBuilder` is used to build conditional or multiple-view UI structures, while `Group` is mainly used to organize existing views or share modifiers without affecting layout.
- Understood that `VStack` creates all child views immediately, whereas `LazyVStack` generates views only when they become visible on screen.
- Realized that `LazyVStack` is more suitable for scrollable, data-driven UIs with many or heavy views because it improves memory efficiency and performance.

---

## 🌐 Web Development Learning

- React Router v7 Framework Mode is similar to Remix, so my Remix experience will still be useful.
- `root.tsx`, `routes.ts`, and route files work together to render each page.

---

## 🔐 TryHackMe Learning

### ContAInment

- Identified useful indicators from attacker notes and used them to recover encrypted files.
- Practiced DFIR-style investigation by following clues across logs, archives, and extracted data.
- Used AI-assisted forensic tools to analyze encoded flag candidates and identify the correct flag.
- Improved my understanding of how AI systems themselves can become targets in modern cyberattacks.

---

# 🚀 Next Week

- Complete the badge algorithm in the SwiftUI tutorial.
- Continue posting small articles on Dev.to and start creating Web UI designs in Figma.
- Continue working on the AI Security Learning Path.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
