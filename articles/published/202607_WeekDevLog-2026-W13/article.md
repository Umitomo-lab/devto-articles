---
title: Weekly Dev Log 2026-W13
published: False
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W13
tags: beginners, devjournal, webdev, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202607_WeekDevLog-2026-W13/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- This week, I mainly focused on iOS development.
- I also tested a small workflow using Codex: organizing ideas, creating a design file, and implementing a SwiftUI prototype. Through that process, I realized that Codex can be very helpful for making iOS development more efficient.
- Until now, I had been using Codex in a rather ad hoc way, sending instructions only when I wanted it to handle a specific task.
- This week, I started thinking about how to make that workflow more efficient, and how to make Codex act more like a development partner that understands the project in the same way I do.
- As I explored this, I realized that I needed to review my Codex settings, build better rule files for giving instructions to Codex, and rethink how I use Codex in my own workflow.
- Working through all of this slightly changed the way I think about AI agents.

---

## 📱 iOS (SwiftUI)

- I organized the UI structure for ToneDrill mini in Figma.
- I created a structured design page and a small Mini Design System in Figma.
- I summarized colors, typography, buttons, fretboard parts, spacing, and radius rules.
- I updated the implementation note so Codex could understand the design direction.
- I asked Codex to implement the SwiftUI fretboard UI based on the Figma design and implementation note.
- I changed the instruction so app colors would be managed as Color Sets in `Assets.xcassets`.
- I reviewed the SwiftUI code for ToneDrill implemented by Codex.
- I asked Codex questions to better understand the implementation.
- I checked how the fretboard UI is drawn and updated in SwiftUI.

---

## 🆙 Updating my workflow

### 🤖 AI agent workflow

- I worked on setting up a more structured workflow for using Codex in my development projects.
- I created a global `AGENTS.md` file for Codex (`~/.codex/AGENTS.md`).
- I created a project-level `AGENTS.md` file at the root of the repository (`repo-root/AGENTS.md`).
- I separated the responsibilities of the global `AGENTS.md` file and the project-level `AGENTS.md` file.
- I created `docs/codex/TaskIndex.md` as a task management document. In it, I organized both immediate tasks and mid- to long-term tasks, and defined a consistent format for writing them down.
- To reduce the need to repeatedly explain the project background, past work, and current tasks every time I move to a new chat, I decided to build a workflow and create a mid- to long-term project memory in Notion for the work and lessons I develop with Codex.
- I created a Notion page called `AI Operating Manual` so AI can summarize the project overview, what I learned, mistakes, improvements, fixes, and any rules that should be added to the project-level `AGENTS.md`. I connected it through Notion MCP so Codex can update it.
- I organized this entire process as a workflow.
- At the start of a chat, Codex should read the `AI Operating Manual` Notion page, then read `AGENTS.md` and `TaskIndex.md`, so it can start working with the same understanding as me. I registered this as a Skill so I can call it with a single phrase.
- At the end of a work session, Codex should summarize what was done and organize what should be saved as mid- to long-term project memory in the `AI Operating Manual` Notion page. I registered this as another Skill so I can call it with a single phrase.
- Finally, I registered a separate Skill that can write the summarized content to the `AI Operating Manual` Notion page. I separated this from the summary Skill so that I can review the content first and decide what should actually be saved as mid- to long-term project memory before running the write operation.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- By asking Codex to implement the SwiftUI UI based on the Figma UI structure and the small design system page, I was able to get a UI that was very close to the design I created in Figma.
- I learned that Codex sometimes adds many custom style definitions in the code, even in areas where SwiftUI’s default styling system would be enough. I need to decide more carefully which parts should rely on SwiftUI’s default styles and which parts should be customized.
- Through this implementation, I learned that I need to separate the parts where I want to take advantage of SwiftUI’s built-in default styles from the parts where I want to apply my own custom design.
- I also noticed that Codex tends to implement SwiftUI previews using older syntax. This helped me understand the difference between older preview code and the newer style I learned in the SwiftUI tutorials.
- I also learned that if I want colors to be managed in `Assets.xcassets`, I need to explicitly tell Codex to do that.
- I learned that I should add rules for Codex so that the same kind of issue does not happen in the next implementation.
- I learned how SwiftUI draws horizontal and vertical lines using `.frame(width:height:)` and `.position(x:y:)`.
- I learned that `.position(x:y:)` places the center of a view.
- I learned that a parent view’s `@State` change causes SwiftUI to recalculate the parent view’s body.
- I learned that child views are updated when new values are passed from the parent view.
- I learned that `@ViewBuilder` does not trigger UI updates by itself.
- `@ViewBuilder` is used to write conditional view logic, such as showing or hiding a view depending on a condition.

---

## 🆙 Updating my workflow Learning

### 🤖 AI agent workflow

#### 🐛 How My Workflow Changed

- Previously, I had to explain in each prompt who I am, how I prefer to work, and what kind of reasoning I expect from Codex. For example, I often had to explain my background and say things like, “Because I think this way, please do not do that.” By organizing this information in advance, I no longer need to repeat those explanations every time, and the direction of Codex’s responses is now much closer to what I expect.
- I can now start talking with Codex about the task I want to work on right away, without wasting time aligning the process. Before, when I felt that Codex was moving in a slightly different direction, I had to explain the project background, current progress, and what I wanted to do next in order to bring Codex back to the same understanding.
- By formatting the workflow, I no longer feel unsure about what information I should give Codex when working on any project. I created a system that lets Codex reach a consistent level of understanding with a minimal prompt. Because I also defined a clear way to operate Codex in order to protect that system, I feel that I can work with it more confidently and without hesitation.

#### 📝 What I Learned From This

- I felt that in order to use an AI agent effectively, I need to clearly tell it who I am and what kinds of actions or workflows I prefer.
- At the same time, I realized that this kind of workflow becomes possible when I clearly define what I will delegate to the AI agent and what I will handle myself. In my workflow, the AI agent should not immediately start working on a task. Instead, it should first propose a plan, and then I, as the human user, review and approve it before the task is executed.
- This feels similar to the relationship between a manager and a team member. In other words, I felt that using an AI agent effectively depends on how well the human can act as a capable manager. I also realized that the skills used to manage work in real-world teams can be useful when working with AI agents.
- For regular applications that are used simply as tools, the important skills are things like understanding the features and knowing how to use the application well.
- I found it interesting that the skills needed for AI agents are different from the skills needed for ordinary tools. This difference feels like one of the unique characteristics of AI agents.

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
