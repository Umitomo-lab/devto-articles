---
title: Weekly Dev Log 2026-W12
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W12
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202606_WeekDevLog-2026-W12/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- 今週は、個人プロダクトに取り組める時間が少なかったが、iOSアプリ開発とWeb開発のプロダクトを少し前進できた。
- 前進できた要因として、ChatGPT、Codexを利用して、効率よく取り組めた点にある。AIの便利さを実感した一週間であった。
- 先週Xcodeで実装したthe minimum-featureのiOSアプリであるToneDrill miniのUI設計を固めていくことを進めた。
- 先週は、Xcodeで最小機能で動くアプリの基本機能面についてわくわくしながら、実装していたが、今週からは、UIイメージ作りに集中した。
- UIイメージの設計方法に悩んだが、AIと相談しながら、方針を決めた。今後も[この進め方](## 📱 iOS (SwiftUI))をベースに思った。
- Web開発は、先週Codexに実装してもらったポートフォリオサイトのプログラムの処理について理解する作業が終わった。
- Shadcn/uiについて、詳しく理解でき、その利便性について理解することができた。
- TryHackMeの演習に取り組めなかったので、来週は取り組めるように頑張る。

---

## 📱 iOS (SwiftUI)

- I used Codex and Figma to create the UI design for the minimum version of ToneDrill mini.
- I asked Codex to generate several UI design ideas, then chose the one I liked and organized it as a design file in Figma.
- ToneDrill mini will have multiple screens in the future, but I focused on designing only one main interaction screen first.
- I started organizing a Mini Design System based on that one screen so that future screens can have a consistent UI.
- At first, I considered organizing the design rules in a text file like `Design.md`, but I decided to organize them visually in Figma instead.
- I organized the basic color structure, including background colors, text colors, button colors, and typography rules.

### 🎸 ToneDrill miniのUIイメージ

FigmaでUIデザインを作成する前の現在のToneDrill miniのUIイメージと今週CodexとFigmaで構築した今のところ暫定したUIイメージを紹介します。
これからこのUIイメージでプログラムを作っていくことを考えてわくわくしています！

_(現在のToneDrill miniのUIのスクリーンショット)_
![ToneDrillmini_UIimage_now](./assets/ToneDrillmini_UIimage_now.png)

_(今週決めたToneDrill miniのUIのスクリーンショット)_
![ToneDrillmini_UIimage_future](./assets/ToneDrillmini_UIimage_future.png)

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to 📝.
- Reviewed the structure of the portfolio home page created with React Router v7.

---

## 🔐 Security (TryHackMe)

- 今週は、取り組むことができなかった。(来週は、取り組めるように頑張りたい！)

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- I noticed that if I ask Codex to create UI designs each time without clear rules, the colors, spacing, and font sizes can easily become inconsistent.
- I learned that it is better to create one base UI design first, then organize the frame structure and Mini Design System based on that design.
- I also considered asking Codex to implement a SwiftUI prototype first and then adjusting it in Xcode, but I felt that organizing the UI visually in Figma first was easier for me to understand.
- Having the UI structure and color roles visible in Figma made it easier to understand the design than organizing everything only in text.
- I learned that a visual design reference also makes it easier to imagine what needs to be changed after implementing the UI in SwiftUI.
- For a personal iOS app like this, I felt that it is better to start with a small set of design rules based on one screen, rather than trying to build a large design system from the beginning.

---

## 🌐 Web Development Learning

- Learned that `sticky top-0` keeps the sidebar content visible near the top of the screen while scrolling.
- Reviewed how Tailwind CSS utility classes are used to control layout in the profile sidebar.
- Learned that `flex flex-wrap` is useful for arranging small elements naturally and letting them wrap when space is limited.
- Learned that `flex` is better for content-sized inline groups, while `grid` is better for structured row-and-column layouts.
- Reviewed the shadcn/ui `Button` component and learned that `asChild` lets a child element, such as an `<a>` tag, receive the button styles while keeping its original HTML meaning.
- Rearned that this makes it possible to create a link that looks like a button, while still using the correct semantic element for navigation.
- Reviewed the official shadcn/ui `Button` documentation and learned how `asChild`, `variant`, and `size` help create consistent button UI patterns.
- Learned that shadcn/ui helps create consistent UI while allowing predefined design variations through component props, and its documentation makes it easy to understand how each prop affects the result.

---

# 🚀 Next Week

- FigmaでToneDrill miniのa Mini Design Systemの整理を完了させる。
- Codexに実装してもらったポートフォリオサイトのUIの微調整を行う為に、微調整箇所をNotionに整理する。UI微調整作業に着手する。
- Continue working on the AI Security Learning Path.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
