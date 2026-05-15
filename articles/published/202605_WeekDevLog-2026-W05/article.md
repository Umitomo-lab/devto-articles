---
title: Weekly Dev Log 2026-W05
published: false
description: Weekly learning log of iOS, web development, and cybersecurity — 2026-W05
tags: beginners, devjournal, security, swift
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202605_WeekDevLog-2026-W05/weekly_dev_cover_image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## 🗓️ This Week

- Made a little more progress in the SwiftUI tutorial.
- Started researching web application technology stacks and creating a roadmap for my long-term goals. I'm moving forward little by little.
- Completed the AI Forensics room from the AI Security Learning Path on TryHackMe this week.

---

## 💡 Thoughts on the AI Forensics Room

The AI Forensics room was much deeper and more challenging than I initially expected, and each task took a significant amount of time to complete. However, it turned out to be an incredibly valuable learning experience 🔥

Task 5, **"Practical - The Digital Trail,"** was especially impressive. It was a story-driven hands-on investigation where I analyzed a compromised company environment after attackers stole critical proprietary source code 🔎

Instead of simply reading explanations, I had to actively investigate logs, suspicious files, reverse shells, persistence mechanisms, and data exfiltration activity step by step.

Because I was constantly thinking, investigating, and connecting the dots myself, the experience felt far more practical and realistic. It gave me a much deeper understanding of how AI-assisted DFIR investigations work in real-world scenarios.

One of the biggest lessons I learned from this room was that **AI is a powerful tool, but human insight is still essential.** AI can quickly detect suspicious activity, but investigators still need to analyze the context and validate the findings themselves.

---

## 📱 iOS (SwiftUI)

- Worked through the SwiftUI tutorial and completed Sections 6 and 7: "Create an Algorithm for Badges"

---

## 🌐 Web Development

- Posted my weekly dev log on Dev.to 📝
- Researched how to transform my current blog site into the portfolio site I want to build in the future.
- Created a roadmap with ChatGPT to gradually turn my blog site into a portfolio site.

---

## 🔐 Security (TryHackMe)

- Completed the AI Forensics room (part of the AI Security Learning Path) on TryHackMe.

---

# 💡 Key Takeaways

## 📱 SwiftUI Review

- Reviewed how SwiftData automatically creates relationships between `@Model` objects through model properties.
- Understood how bidirectional relationships work between `Moment` and `Badge` models.
- Learned that `Group` is useful when applying modifiers to conditionally displayed views.
- Realized that SwiftUI modifiers can only be attached to actual views, not directly to an `if` statement.
- Reviewed how `@ViewBuilder` allows a custom SwiftUI view to accept and display child views passed from outside.
- Understood that `.offset(y:)` moves a view from its original position to fine-tune layouts.

---

## 🔐 TryHackMe Learning

### AI Forensics Task 3 — AI & DFIR

- Learned how AI and machine learning are transforming modern DFIR investigations.
- Studied how CNN models can detect image tampering and manipulated content.
- Learned how machine learning is used in dynamic malware analysis.
- Understood that API call sequences represent program behavior patterns.
- Studied how API sequences can be converted into 2D images for AI analysis.
- Learned why CNN-based image recognition models can classify malware behavior.
- Learned how NLP models help identify phishing emails and suspicious communications.
- Understood how AI can reconstruct incident timelines from fragmented evidence.
- Studied how AI accelerates forensic analysis and improves detection capabilities.
- Understood that AI enhances human investigators rather than replacing them.
- Learned the importance of combining AI-assisted analysis with human expertise in cybersecurity.

### AI Forensics Task 4 — AI Legal & Ethical Implications

- Learned that AI in forensics must be explainable and defensible in court.
- Understood how “black box” AI models can weaken the credibility of digital evidence.
- Learned that biased AI systems can lead to real-world injustice and wrongful accusations.
- Studied the importance of maintaining chain of custody and audit trails when using AI in DFIR.
- Understood why undocumented AI processing can make forensic evidence legally challengeable.
- Learned that privacy and legal compliance are critical when handling sensitive evidence with AI tools.
- Studied how Federated Learning and offline AI environments help preserve privacy.
- Learned that AI should enhance human investigators, not replace human judgment and responsibility.

### AI Forensics Task 5 — Practical: The Digital Trail

- Learned how AI and machine learning can support DFIR investigations by identifying suspicious logs and files.
- Studied how attackers use reverse shells to gain and maintain remote access to compromised systems.
- Learned how hidden files, `/tmp`, and `/dev/shm` are commonly abused for stealth and persistence.
- Understood how attackers disguise malicious tools as legitimate system utilities to evade detection.
- Studied how SSH key abuse and `authorized_keys` modification can enable stealthy privilege escalation.
- Learned how fake telemetry logs and masquerading techniques help attackers blend into normal environments.
- Understood how compressed and Base64-encoded archives can be staged for data exfiltration.
- Learned how DFIR investigations connect evidence from logs, bash history, suspicious files, and network activity.
- Studied how AI can misclassify legitimate files as suspicious, highlighting the importance of human validation.
- Learned that AI enhances investigations, but human reasoning and contextual analysis remain essential in DFIR.

---

# 🚀 Next Week

- Complete the badge algorithm in the SwiftUI tutorial.
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
