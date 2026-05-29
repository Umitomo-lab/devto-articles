---
title: Weekly Dev Log 2026-W07
published: True
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W07
tags: beginners, devjournal, security, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202605_WeekDevLog-2026-W07/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Completed two more sections of the SwiftUI tutorial 🦾 As I continue working through the tutorial, I can feel my understanding of **SwiftUI fundamentals becoming more solid**🔥
- It was **my first time posting a standalone article** about reverse engineering📝 If you're interested, feel free to check it out 👇
  {% link https://dev.to/umitomo-lab/a-curious-journey-into-reverse-engineering-an-ai-generated-python-exe-1n0b %}
- **I started creating UI designs for my future portfolio website in Figma.** I was able to roughly sketch out the overall structure of the site, but I also realized **how difficult it is to create modern and stylish UI designs.** (It really made me realize I don’t have much design sense yet 😂💦)
- While struggling with the design process, I came across several articles about **Figma MCP**. That made me interested in exploring how generative AI could help with UI design ideas, so **I decided to start researching Figma MCP further.**
- Completed **Securing AI Systems** room from the AI Security Learning Path on TryHackMe this week🤖

---

## 📱 iOS (SwiftUI)

- Worked through the SwiftUI tutorial and completed "Create an Algorithm for Badges" and "Add inclusive features"

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to and a standalone article about my first attempt at reverse engineering 📝
- Created rough portfolio website UI layouts in Figma
- Used shadcn/ui component library design templates in Figma
- Started learning UI design in Figma using community resources

---

## 🔐 Security (TryHackMe)

- Completed Securing AI Systems room (part of the AI Security Learning Path) on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Add inclusive features

- Learned that SwiftUI automatically adapts UI elements for Light and Dark Mode by default.
- Learned how to preview and compare Light and Dark Mode layouts in the Xcode canvas.
- Understood that system-provided semantic styles help SwiftUI automatically adjust UI appearance.
- Learned that SwiftUI uses view modifiers to customize `ScrollView` behavior.
- Understood that `.scrollBounceBehavior(.basedOnSize)` only enables bouncing when the content is larger than the visible area.
- Learned that `.defaultScrollAnchor(.center, for: .alignment)` centers smaller content inside a `ScrollView`.
- Learned that the `dynamicTypeSize` modifier can be applied to any SwiftUI view.
- Learned how `AttributedString(localized:)` supports localization-aware text in SwiftUI.
- Understood that `(inflect: true)` automatically changes words like “Day” and “Days” based on the number value.
- Learned that SwiftUI can apply different font styles to specific parts of an `AttributedString`.
- Realized that Apple provides built-in grammar inflection support for more natural localized UI text.

---

## 🌐 Web Development Learning

- Reviewed several useful functions in Figma
- Learned the importance of focusing on the overall page layout before designing detailed UI components

---

## 🔐 TryHackMe Learning

### Securing AI Systems

#### Task 2 Anatomy of an AI System

- Traditional apps use deterministic logic, while AI systems rely on probabilistic model inference.
- AI systems accept free-form natural language, making input validation much harder.
- Prompt Construction combines the system prompt, user input, and retrieved context before sending data to the LLM.
- **RAG** allows LLMs to retrieve external knowledge from a vector store or other data sources.
- A vector store contains embedded representations of internal documentation for retrieval-augmented generation (RAG)
- Trust boundaries are points where data moves between different security contexts.
- Major trust boundaries include user-to-system, system-to-LLM, LLM-to-tools, and system-to-user.
- LLM-to-tools is especially sensitive because model output can trigger real actions.
- Tool layers may execute database queries, API calls, or file operations on behalf of the LLM.
- Security controls are needed at every boundary to reduce prompt injection and data leakage risks.

#### Task3 The AI Attack Surface

- Studied the **OWASP LLM Top 10** and how major risks affect AI-integrated systems.
- Learned that **MITRE ATLAS** documents adversary tactics and exploitation techniques for AI systems.
- Studied how **the NIST AI RMF** approaches AI security from a governance and risk management perspective.
- Learned the difference between OWASP (vulnerabilities), ATLAS (attack techniques), and NIST AI RMF (risk governance).

#### Task4 System-Level Threats

- Studied how LLM10 Unbounded Consumption can cause resource exhaustion and extreme cost increases through excessive requests.
- Learned that system prompts may leak internal rules, tool information, and architecture details if exposed.(LLM07).
- Understood that LLM output must never be trusted as safe input for downstream systems.(LLM05)
- Learned that Excessive Agency occurs when AI systems are given unnecessary permissions, tools, or autonomy.(LLM06)
- Learned that users may unintentionally leak sensitive information when using AI systems.(LLM02)
- Studied how the OWASP LLM risks relate to the CIA triad across confidentiality, integrity, and availability.

#### Task 5 Secure Design Patterns

- Learned that security controls are most effective when applied during the design stage of AI systems.
- Learned that layered controls reduce the risk of end-to-end attack success.
- Understood **the importance of least privilege for AI tools, API tokens, and database access.**
- Learned that write operations should require human approval before execution.
- Studied how input and output validation reduce **prompt injection** and downstream injection risks.
- Learned that **MLSecOps** integrates security throughout the AI and machine learning lifecycle.

---

# 🚀 Next Week

- Complete the badge algorithm in the SwiftUI tutorial.
- Continue posting small articles on Dev.to.
- Explore Figma MCP and experiment with generating UI design ideas using AI.
- Continue working on the AI Security Learning Path.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
