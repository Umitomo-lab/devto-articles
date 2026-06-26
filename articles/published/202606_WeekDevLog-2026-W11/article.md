---
title: Weekly Dev Log 2026-W11
published: False
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W11
tags: beginners, devjournal, security, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202606_WeekDevLog-2026-W11/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- While reviewing the code for **the minimum-feature iOS app** that Codex implemented for **ToneDrill**, I started coming up with **many ideas for small improvements**💡.
- When I first started building the iOS app, I thought **it would be enough to recreate the web version** I had casually built before. However, once the app started taking shape, I naturally began wanting to add **more features and improve the design**🌋. At the same time, this is **my first time building an iOS app**, so I often **do not know the best way to move forward**. Human curiosity and ambition are interesting 😅.
- Because of that, I discussed my ideas with ChatGPT, **separated them into short-term tasks and medium- to long-term ideas**, and **organized a realistic development plan** in Notion🗃️.
- For now, I decided to focus on **completing the minimum-feature version implemented by Codex**. I changed the app layout from the default portrait orientation to landscape orientation and organized several UI ideasideas🦾.
- I **reviewed the program** that Codex implemented last week based on my Figma design.
- I learned more about **React Router v7 features and several CSS functions**.
- Worked on the **AI System Reconnaissance** room from the AI Security Learning Path on TryHackMe this week 🤖.

---

## 📱 iOS (SwiftUI)

- Organized feature ideas I would like to add to ToneDrill in Notion and separated them into short-term tasks and medium- to long-term tasks.
- Changed the app layout from the default portrait-oriented design to a landscape-oriented design.
- Planned the next UI improvement for the app: replacing horizontal scrolling with left and right buttons to switch the visible fret range.
- Explored a design direction for a SwiftUI-drawn guitar fretboard background before using a real image background.
- Worked with ChatGPT to define the direction for a fretboard-style UI in SwiftUI, organized the required display elements, and prepared them as a specification for Codex.
- Prepared a concrete Codex prompt for generating a Figma draft based on the design task document and reference image.

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to 📝.
- Reviewed the structure of the portfolio home page created with React Router v7.
- Checked how `root.tsx`, `routes.ts`, and `home.tsx` work together to render the top page.
- Studied how the `loader` function passes page data to the home component.
- Looked through `home-page-layout.tsx` and checked how the main area and profile sidebar are arranged.
- Reviewed `app.css` to understand the layout, responsive design, and light/dark color settings.
- Looked up `grid-template-columns`, `minmax()`, `clamp()`, and `@media` using MDN and ChatGPT.

---

## 🔐 Security (TryHackMe)

- Worked on the AI System Reconnaissance room, part of the AI Security Learning Path on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- Learned how to configure an iOS app to support landscape orientation.
- Learned how to adjust the UI layout so it fits neatly on the screen in landscape mode.
- Learned that a SwiftUI-drawn fretboard background is a safer first step than placing buttons directly on top of a real guitar image.
- Learned that building the fretboard UI with separate background and button layers will make it easier to replace the background with an image later.
- Learned that Codex should first explain its planned Figma structure before actually creating or modifying the design.
- Learned that giving Codex a task document, a reference image, and clear constraints helps reduce unexpected changes.

---

## 🌐 Web Development Learning

- Learned that `root.tsx` provides the base HTML layout, and child routes are rendered through `<Outlet />`.
- Learned that `loader` prepares data before the page component is rendered.
- Learned that `home-page-layout.tsx` mainly controls the page structure, while `app.css` controls most of the visual design.
- Learned how CSS Grid is used to create a two-column layout with a flexible main area and a fixed-width sidebar.
- Learned that `grid-template-columns` defines the width rules for each grid column.
- Learned that `minmax()` sets the minimum and maximum size of a grid column.
- Learned that `clamp()` lets a value change flexibly within a minimum and maximum range.
- Learned that `@media` rules can be used for different CSS conditions. In this project, they are used to change the layout based on the screen width.
- Learned how media queries change the layout from three-column cards to two columns, and then to one column on smaller screens.
- Learned how CSS variables are used to manage colors for light mode, dark mode, and portfolio-specific design tokens.

---

## 🔐 TryHackMe Learning

### AI System Reconnaissance

#### Task 2: The AI Infrastructure Stack

- I learned that AI infrastructure is not just a single AI model or server, but a collection of specialized services that support the whole machine learning lifecycle.
- I understood that AI systems often expose unfamiliar ports and APIs, so traditional network scanning alone may miss important AI-related services.
- I learned that services such as model serving endpoints, experiment tracking tools, vector databases, model registries, Jupyter notebooks, MinIO, and Prometheus can all become important reconnaissance targets.
- Although there were many new terms and I could not fully understand every single one, I was able to understand the main purpose of this task: building a mental map of AI infrastructure components and their common ports.
- Through the exercise, I learned how to compare AI-specific ports with traditional service ports and identify which hosts are likely running AI infrastructure.

---

# 🚀 Next Week

- Design the UI structure for the minimum-feature version of ToneDrill in Figma.
- Finish reviewing the program that Codex implemented last week based on my Figma design and deepen my understanding of how the code works.
- Continue working on the AI Security Learning Path.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
