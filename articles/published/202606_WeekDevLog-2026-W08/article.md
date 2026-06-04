---
title: Weekly Dev Log 2026-W08
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W08
tags: beginners, devjournal, security, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202606_WeekDevLog-2026-W08/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Completed one section of the SwiftUI tutorial 🦾 Since I want to continue through the tutorial until **I can build the app for testing and run it on an actual iPhone**, I’ll focus on that from next week.
- I also wrote another standalone article this week. It was about **my experience experimenting with Codex and Figma MCP to see how much UI design work I could delegate to AI**📝 If you're interested, feel free to check it out 👇
  <!--{% link https://dev.to/umitomo-lab/a-curious-journey-into-reverse-engineering-an-ai-generated-python-exe-1n0b %}-->
- I’ll continue working steadily on my portfolio site design by combining AI-generated UI ideas with the official shadcn/ui Figma design template.
- Completed **LLM Security** room from the AI Security Learning Path on TryHackMe this week🤖

---

## 📱 iOS (SwiftUI)

- Worked through the SwiftUI tutorial and completed "Reproduce a bug with unit tests"

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to and a standalone article about my experience using Codex × Figma MCP 📝
- Started learning UI design in Figma using community resources

---

## 🔐 Security (TryHackMe)

- Completed LLM Security room (part of the AI Security Learning Path) on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### Reproduce a bug with unit tests

- Learned that a streak should only increase when a moment exists on the next consecutive day.
- Understood that multiple moments on the same day should not increase the streak more than once.
- Learned how `continue` skips duplicate days while keeping the current streak.
- Realized that `break` stops the calculation as soon as a gap in the streak is found.
- Learned that fixing one bug can accidentally introduce new bugs in other scenarios.
- Learned how to implement parameterized unit tests by preparing multiple input patterns and expected values.
- Used `@Test(arguments:)` to run the same test logic with different test data.
- Used `#expect` to compare the actual result with the expected value for each case.

---

## 🌐 Web Development Learning

- While experimenting with automating UI design using Codex × Figma MCP, I learned that clearly defining design system rules first and then building the UI from small components is important for reducing the gap between the original Figma design and the implementation generated from its design data.

---

## 🔐 TryHackMe Learning

### LLM Security

### Threat Categories

#### Data-Based Threats

- Training data extraction
- Membership inference
- Prompt leakage

#### Model-Based Threats

- Model extraction
- Model inversion

#### System-Based Threats

- Prompt injection
- Context Overflow
- Memory Poisoning

#### User-Based Threats

- LLM-powered social engineering
- Trust exploitation

### LLM Security Threat Cheat Sheet

| Type             | Threat                                                    | Target / Attack Surface                        | Input                                                              | Output                                                                              |
| ---------------- | --------------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| **Data-Based**   | **Training Data Extraction**                              | Training dataset (confidentiality)             | Crafted prompts designed to trigger memorised content              | Verbatim or near verbatim training data (text, PII, secrets)                        |
| **Data-Based**   | **Membership Inference**                                  | Training dataset membership (privacy metadata) | Known candidate data sample already possessed by the attacker      | Yes/no (or probability) decision indicating whether the sample was used in training |
| **Data-Based**   | **Prompt Leakage / System Prompt Exposure (LLM07:2025)**  | System prompt / developer instructions         | Prompts asking the model to reveal or reflect on its instructions  | Partial or full disclosure of hidden system or developer prompts                    |
| **Model-Based**  | **Weight Extraction (Model Stealing)**                    | Model parameters (intellectual property)       | Large volumes of carefully chosen API queries                      | A surrogate or distilled model replicating the original model's behaviour           |
| **Model-Based**  | **Model Inversion**                                       | Model's internal representations               | Unknown or partially known data, or model embeddings/outputs       | New training data or attributes reconstructed from the model                        |
| **System-Based** | **Context Window Poisoning (Prompt Injection)**           | LLM context window (instruction hierarchy)     | Attacker controlled text embedded in input or retrieved content    | Altered behaviour, policy bypass, unintended actions                                |
| **System-Based** | **Context Overflow / Unbounded Consumption (LLM10:2025)** | Context window size and system resources       | Excessively large prompts or documents                             | Truncated safeguards, degraded responses, or denial of service                      |
| **System-Based** | **Stateful Conversation Manipulation (Memory Poisoning)** | Persistent conversation memory                 | Malicious statements intended to be stored as long term context    | Persistent misinformation or corrupted future responses                             |
| **User-Based**   | **LLM-Powered Social Engineering**                        | Human cognition and decision-making            | Contextual or personal information used to craft persuasive output | Manipulated users (phishing success, fraud, coerced actions)                        |
| **User-Based**   | **Trust Exploitation / Misinformation (LLM09:2025)**      | User trust and judgment                        | Confident but incorrect or maliciously framed prompts              | Users accepting false, unsafe, or harmful information                               |

### Key Takeaways

- **LLMs introduce a unique attack surface** distinct from traditional ML systems, driven by natural language interaction, context handling, and emergent behaviour.
- **Data-based threats** exploit how LLMs learn from and memorise training data, enabling attacks such as training data extraction, membership inference, and system prompt leakage.
- **Model-based threats** target the model itself, including model extraction (theft of model behaviour or weights) and model inversion (reconstructing sensitive training data).
- **System-based threats** arise from how LLMs process all inputs as a single context, enabling prompt injection, context window overflow, and memory poisoning.
- **User-based threats** leverage LLMs as force multipliers for social engineering, increasing the effectiveness of phishing, scams, and trust exploitation.

---

# 🚀 Next Week

- Work through the "Preparation for Distribution" section of the SwiftUI tutorial.
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
