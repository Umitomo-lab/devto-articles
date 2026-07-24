---
title: Weekly Dev Log 2026-W15
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W15
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202607_WeekDevLog-2026-W15/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Summer has fully arrived in Japan, and people are enjoying the season in many ways, from local festivals to swimming pools🌊. **Just like last week, work has stayed hot in more ways than one**💦, but I have still been **finding small pockets of time to move my projects forward little by little**🐛. I want to **keep growing at my own pace without rushing**✨.
- This week, I was able to **make progress on the iOS app development** for ToneDrill. Based on **the top menu UI design** I created in **Figma** last week, I implemented the screen in **SwiftUI**⛏️.
- I asked **Codex** to implement it **using the same workflow** I used when building **the first screen with the app’s main feature**. This time as well, **Codex helped me implement the SwiftUI screen closely based on the Figma UI design**🦾.
- However, some detailed adjustments still **require human review** and **manual refinement**. I will continue **reviewing the implementation myself** while learning more about the overall iOS app development flow and SwiftUI implementation.
- Since **Codex** handles the overall implementation structure, I can **move forward with iOS app development while saving a significant amount of time**. This has made me feel the **usefulness of AI even more clearly**.
- I was also able to **complete one TryHackMe task for the first time in two weeks**😂. The room I am currently working on also covers **infrastructure used in AI applications**, so **there are many unfamiliar terms**. Even so, I want to **keep making progress little by little while researching them as I go**🔍.

---

## 📱 iOS (SwiftUI)

- Organized the structure of the top menu screen in Figma.
- Created designs for both the main top menu and the submenu screen that opens when a menu button is selected.
- Defined a “Coming Soon” state for features planned for future development and established a corresponding color palette.
- Created the SVG icons used on the menu screens in Figma.
- Added the new colors and icons from the design process to `Assets.xcassets`.
- Organized `Assets.xcassets` into separate folders for colors and images.
- Implemented the Top Menu and Practice Mode screens in SwiftUI.
- Added reusable menu card styles and layout settings.
- Connected the screens using `NavigationStack` and `NavigationLink`.
- Added disabled “Coming Soon” cards for future features.
- Documented the implementation and prepared an Xcode verification checklist.
- Reviewed the Xcode result and found that the `NavigationStack` navigation bar pushed `FretboardPracticeView` downward, clipping the `Answer` and `Next` area.
- Hid the Back button and navigation bar using `.navigationBarBackButtonHidden(true)` and `.toolbar(.hidden, for: .navigationBar)`.
- Added a custom `Quit` button that presents an alert before calling `dismiss()` to return to `PracticeModeView`.

---

## 🔐 Security (TryHackMe)

- Worked on the AI System Reconnaissance room, part of the AI Security Learning Path on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- Reviewed how to add new Color Sets and Image Sets to `Assets.xcassets`.
- Visually distinguishing between enabled and disabled menu components helped clarify the intended result before implementing the screens in SwiftUI.
- I was reminded that using Codex to edit and organize Figma designs through MCP is an efficient way to break down an existing UI concept into detailed, implementation-ready specifications.
- Parent views should decide a card’s state, layout, and destination.
- Reusable views can translate configuration values into visual styles.
- `MenuCardState` is a display setting, not the same as SwiftUI’s `@State`.
- Keeping navigation outside reusable UI components makes responsibilities clearer.
- Figma designs should be adapted to responsive SwiftUI layouts instead of copied as fixed coordinates.
- `NavigationStack` manages the screen hierarchy, while `NavigationLink` opens each destination.
- `GeometryReader` lets a view calculate its layout from the space currently available to it.
- Destination views are not placed inside the Top Menu’s `GeometryReader`; they receive their own layout space when presented by `NavigationStack`.
- Adding `NavigationStack` can change the available layout height, even when the destination view itself is unchanged.
- Navigation changes must be reviewed together with the destination screen’s existing size and safe-area assumptions.
- A practice or game screen may need a protected exit flow instead of the standard Back button.
- The destination view should control its own navigation-bar visibility when it requires a full-height layout.

---

## 🔐 TryHackMe Learning

### AI System Reconnaissance

#### Task 3: Fingerprinting AI Services

- I learned that finding an open port is only the first step. To understand what is actually running behind the port, I need to fingerprint the service.
- I learned that standard Nmap service detection is not always enough for AI infrastructure because AI services can be mislabeled as generic HTTP services or unknown gRPC services.
- I understood that AI service fingerprinting requires checking multiple clues, such as HTTP headers, JSON response structures, error messages, endpoint names, and gRPC behavior.
- I learned that some AI frameworks reveal their identity through response headers. For example, TorchServe may return a `Server: TorchServe` header, while Triton can expose Triton-specific headers and telemetry information.
- I learned that API responses can also reveal the framework. For example, OpenAI-compatible endpoints often return JSON containing fields such as `"object": "model"`.
- I understood that error messages can be useful for fingerprinting because AI frameworks often return detailed debugging information about tensor shapes, data types, or internal namespaces.
- I learned that AI-related endpoints often use names such as `/predict`, `/infer`, `/generate`, `/embeddings`, `/v1/models`, and `/v2/models`, which are different from traditional REST endpoints like `/users` or `/products`.
- I learned that some AI services expose gRPC in addition to HTTP, and normal HTTP scanners may miss these services because gRPC is a binary protocol.
- I understood that `grpcurl` can be used to inspect gRPC services, and if gRPC reflection is enabled, it may reveal the available services and API schema.
- I learned that fingerprinting does not always require exploitation. Even simple requests, harmless prompts, headers, and response formats can reveal what model or framework is running behind an endpoint.
- Through the exercise, I learned how to move from “this port is open” to “this service is likely Triton, MLflow, Qdrant, or Jupyter” by checking service-specific responses.

---

# 🚀 Next Week

- Continue developing the top menu screen for ToneDrill.
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
