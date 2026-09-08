---
title: Weekly Dev Log 2026-W18
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W18
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

- We’ve still had plenty of hot days lately, but there have also been some cooler days when it rains. It’s starting to feel like summer is slowly coming to an end🎇.

- **Work has been quite busy recently**, and I haven’t been able to find as much time as I’d like for my own development projects💦. Because of that, **it’s been about two weeks since my last Weekly Dev Log update**.

- By my previous update, I had mostly finished **Note Practice**, the first practice mode in ToneDrill. So I’ve now started working on the next feature, **Chord Tone Practice**🦾.

- In Chord Tone Practice, I want the player to find chord-tone patterns on the guitar fretboard based on the selected root note and chord quality, Major or Minor🎸. For example, a Major chord can generate not only `1-3-5`, but also patterns such as `3-5-1` and `5-1-3`. The player finds one correct note position on each of three consecutive strings.

- Personally, I really enjoy practicing simple chord tones using only the Root, 3rd, and 5th on the guitar, so that was one of the reasons I wanted to build this mode😂. I like how just a few notes can still create a clear and beautiful chord sound🎵.

- This week, **I worked with Codex to define the game rules in much more detail**💡. While deciding things like the root notes, Major / Minor chord qualities, chord-tone patterns, strings to use, and how correct answers should be counted, I started wondering: **“Will these rules actually work under every possible condition?”**

- So before implementing the feature in SwiftUI, I had Codex create a separate JavaScript validation script to test the game rules first.

- The script checked **504 different conditions**, combining 12 root notes, Major / Minor chord qualities, three chord-tone patterns, and seven visible fret ranges.

- The results confirmed that there were no cases with zero valid answers, no overlapping answer positions, and no situations where the player could get stuck before completing all valid answers.

- The ToneDrill app itself is being developed in Swift and SwiftUI, so using a separate JavaScript program only to validate the game rules before implementation was **a new and interesting approach for me**🤔.

- I also became curious about how the JavaScript script was actually checking all 504 conditions. I started debugging the code and asking Codex questions about each part of the process, and before I knew it, I had spent quite a lot of time on it 😅

- Still, it turned out to be a useful detour because I was able to learn more about how the JavaScript code worked as well🐛.

- Now that the basic game rules are settled, **the next step is to work on the UI**🔥. I’m looking forward to seeing how the practice mode feels once it starts taking shape on screen✨.

- About a month ago, I was able to keep up with both development and my weekly Dev.to posts fairly consistently. Recently, though, work has been much busier, and **there have been many days when I haven’t been able to make as much progress as I wanted**.

- Still, I want to remember why I started doing this in the first place: because I enjoy **building things** and **learning things I didn’t know before**.

- Rather than comparing myself too much with other amazing developers, **I want to keep moving forward one step at a time at my own pace**🚶. Lately, **I’ve been reminded again of how important that is**🌱.

---

## 📱 iOS (SwiftUI)

- Defined and reviewed the core rules for the new **Chord Tone Practice mode**.
- Finalized the root, chord quality, degree pattern, and valid answer rules.
- Used an AI-generated JavaScript script to validate all **504 planned conditions** before Swift implementation.
- Reviewed the validation script to understand how it generated answer sets and checked edge cases.
- Debugged the script with breakpoints and conditional breakpoints to trace specific test cases.
- Documented the script’s execution flow, validation logic, and important JavaScript concepts in a separate Markdown learning note.

---

# 💡 Key Takeaways

- I learned that a separate validation program can be useful for checking game rules before implementing them in the main application.
- I learned that reviewing AI-generated validation code is important, not just checking whether the final result says “passed.”
- I gained a better understanding of how the script used `map()`, `filter()`, `flatMap()`, `reduce()`, `some()`, `every()`, `Set`, `Map`, and bit masks.
- I learned how conditional breakpoints can help isolate one specific case from many repeated test combinations.
- Debugging the script helped me understand its execution flow much more clearly than simply reading the code.
- The investigation gave me more confidence in the Chord Tone Practice rules before moving on to the Swift implementation.

---

# 🚀 Next Week

- Continue designing the UI for **Chord Tone Practice**
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
