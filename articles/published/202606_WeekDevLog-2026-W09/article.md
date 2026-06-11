---
title: Weekly Dev Log 2026-W09
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W09
tags: beginners, devjournal, security, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202606_WeekDevLog-2026-W09/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- **Completed the SwiftUI app development tutorial** and tested the app I built on a real iPhone🦾
- Learned **the overall flow of building an iOS app with SwiftUI**.
- Organized my app ideas in Notion because I want to start building a real app next week🤔 I also realized that **starting with a small app** is important at this stage💡
- Worked on the UI design for my portfolio site using the official shadcn/ui Figma template. I want to finish one design direction next week and then move on to implementation.
- Worked on the **AI Threat Modelling** room from the AI Security Learning Path on TryHackMe this week🤖

---

## 📱 iOS (SwiftUI)

- Completed the SwiftUI app development tutorial.
- Learned how to run an app on a real iPhone by connecting it to my computer, without joining the Apple Developer Program yet.

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to📝
- Worked on my portfolio site UI design using the official shadcn/ui Figma template.

---

## 🔐 Security (TryHackMe)

- Worked on the AI Threat Modelling room (part of the AI Security Learning Path) on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

### What I learned from testing an app on a real iPhone🔬

- I need to connect my iPhone, choose it as the run destination, and configure Signing & Capabilities before running the app.
- A unique Bundle Identifier is needed to identify the app.
- Xcode uses my personal Apple Account to sign the app for testing on my iPhone.
- I need to enable Developer Mode and trust the developer profile on the iPhone before launching the app.
- Preview data and real app data are handled differently in SwiftUI/SwiftData.
- In previews, `sampleContainer` is used, so `includeSampleMoments` is passed as `true`.
- The diary entries I create on the real iPhone are saved in the app’s local storage on the device.
- The data is not automatically saved to my Apple Account or iCloud.

### What I learned from organizing ideas for my first iOS app🦄

- As a beginner developer, I should not try to build a large, market-ready app from the beginning.
- Large apps usually include many hidden complexities, such as data management, user experience design, error handling, security, performance, and long-term maintenance.
- Since I have a full-time job, my development time is limited, so starting too big would make it harder to keep making steady progress.
- Starting with a small app helps me focus on one or two core ideas and understand each part more deeply.
- Building something small first also makes it easier to finish, test, and improve the app step by step.
- I realized that the goal at this stage is not to compete with polished apps on the market, but to build practical experience by completing small projects.
- This approach should help me stay motivated while gradually improving my skills in real app development.

---

## 🌐 Web Development Learning

- Learned more about how to create UI designs in Figma and how to design screens using components.
- Practiced building a consistent portfolio site design based on a design system instead of creating each part separately.

---

## 🔐 TryHackMe Learning

### AI Threat Modelling

#### Task2 AI-Specific Assets and Attack Surfaces

- AI systems add new assets such as training data, model weights, embedding vectors, system prompts, feature stores, and model registries.
- I learned that poisoned training data can corrupt a model’s behaviour at the source.
- I learned that model weights are especially valuable because they define what the model has learned.
- If model weights are stolen, an attacker may obtain a functional copy of the AI system.
- I learned that system prompts can reveal the model’s behaviour, constraints, business logic, and security guardrails.
- Embedding vectors are important in systems such as RAG pipelines, recommendation engines, and fraud detection systems.
- Manipulating embeddings can change what information the model sees at query time.
- Feature stores are important because they provide preprocessed data used as real-time model inputs.
- Tampering with feature stores can affect model decisions without changing the model itself.
- A compromised model registry can allow an attacker to replace a legitimate model with a backdoored one.
- AI threat modelling needs to consider not only traditional application risks, but also AI-specific assets, behaviours, and failure modes.

#### Task3 Data Supply Chain and STRIDE's Gaps

- I learned that AI systems have a data supply chain in addition to a traditional software supply chain.
- Each stage of the AI data supply chain can become a point of compromise.
- Data poisoning can start from data collection, labelling, or other early pipeline stages.
- If poisoned data reaches training, the damage can become embedded in the model’s weights.
- A compromised model registry can allow attackers to replace a validated model with a backdoored one.
- A backdoored model may look normal until it receives specific trigger inputs in production.
- LLM-based systems can introduce additional injection points through retrieval pipelines during inference.
- AI threats such as data poisoning, adversarial manipulation, tool misuse, and model theft do not always fit neatly into traditional STRIDE categories.
- The key takeaway is that AI threat modelling must cover the full data supply chain and AI-specific failure modes.

#### Task4 Adapting STRIDE for AI Systems

- I learned that STRIDE does not need to be replaced, but it needs to be adapted for AI systems.
- In AI systems, familiar STRIDE categories can appear in new forms, such as data source impersonation, data poisoning, model extraction, and inference cost exploitation.
- AI decisions are harder to audit because the model version, input features, prompts, and retrieved context may not be fully recorded.
- Tool-enabled AI systems can make privilege risks broader, because a jailbroken model may misuse databases, email systems, or other connected tools.
- The key takeaway is that STRIDE is still a useful starting point, but some AI risks require additional AI-specific frameworks such as MITRE ATLAS.

#### Task5 MITRE ATLAS: The AI Threat Technique Catalogue

- I learned that MITRE ATLAS is an AI-focused knowledge base for adversary tactics and techniques against AI and ML systems.
- ATLAS complements STRIDE by adding AI-specific technical detail, documented techniques, mitigations, and real-world case studies.
- I learned key ATLAS techniques such as Data Poisoning, Model Extraction, Evade ML Model, LLM Prompt Injection, and Backdoor ML Model.
- ATLAS helps turn broad STRIDE findings into specific, actionable threat findings with technique IDs and defensive guidance.
- Real-world cases such as ShadowRay and Morris II show that AI threats are not only theoretical, but can affect real AI infrastructure and RAG-based systems.

---

# 🚀 Next Week

- Start building a small iOS app based on the app ideas I organized this week.
- Finish one portfolio site UI design in Figma and start implementing it in code.
- Continue posting small articles on Dev.to.
- Continue working on the AI Security Learning Path.

---

# 🌈 Goals for This Year

## 📱 iOS (SwiftUI)

- Build a solid foundation in SwiftUI and create at least one iOS app.

## 🌐 Web Development

- Continue posting learning logs on Dev.to and eventually turn them into a portfolio site using React Router v7.

## 🔐 Security (TryHackMe)

- Continue learning cybersecurity on TryHackMe.
