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

暑い日が続く一方で、雨が降ると少し涼しく感じる日も増え、少しずつ夏の終わりを感じるようになってきました。

ここ最近は仕事がかなり忙しく、自分の開発に使える時間をなかなか確保できませんでした。その影響もあり、このWeekly Dev Logを更新するのも約2週間ぶりです。

前回の更新までに、ToneDrillの最初の練習メニューである **Note Practice** を一通り完成させることができました。そこで次の機能として、現在は **Chord Tone Practice** の開発を進めています。

Chord Tone Practiceでは、選択したRootとMajor / Minorをもとに出題されるコードトーンのパターンを、ギター指板上から探す練習を作ろうとしています。例えばMajorであれば、`1-3-5` だけでなく、`3-5-1` や `5-1-3` といった並びも問題として出題します。プレイヤーは連続する3本の弦から、それぞれ正しい音の位置を1つずつ探して回答します。

個人的に、ギターでRoot・3rd・5thだけを使ったシンプルなコードトーンを弾く練習が結構好きなので、それをそのまま練習できるような機能を作ってみたいと思ったのが、このモードを考えたきっかけの一つです。少ない音だけでもきれいにコード感が出るところが好きです。

今週は、Codexと相談しながらこのゲームルールをかなり細かく整理しました。RootやMajor / Minor、コードトーンの並び、使用する弦、正解数の数え方などを決めていく中で、「このルールで本当にすべての条件で問題を作れるのか？」という疑問も出てきました。

そこで、SwiftUIで実装を始める前に、CodexにJavaScriptの検証プログラムを作ってもらい、考えたルールそのものを先に検証しました。

検証では、12種類のRoot、Major / Minor、3種類のコードトーンパターン、7種類のフレット表示範囲を組み合わせた **全504条件** を確認しました。その結果、正解が1つも存在しない条件や、正解位置の重複によって途中で回答できなくなるケースなどがないことを確認できました。

アプリ本体はSwift / SwiftUIで作っていますが、実装前のルール検証だけを別のJavaScriptプログラムで行う、という進め方は自分にとってかなり新鮮でした。

ちなみに、このJavaScriptがどのように504条件を調べているのか気になり、コードをデバッグしながらCodexに処理内容を質問していたら、それだけでかなり時間を使ってしまいました（笑）。ただ、JavaScriptの処理についても勉強できたので、結果的には良い寄り道だったと思います。

ゲームの基本ルールを固めることができたので、次はUIを形にしていきます。実際に画面として動き始めたときに、どんな練習モードになるのか自分でも楽しみです。

1か月ほど前までは毎週かなり安定して開発とDev.toへの投稿を続けられていましたが、最近は仕事が忙しく、思うように時間を取れない日が続いています。

それでも、最初から大きな成果を求めるのではなく、そもそも自分は「何かを作ること」と「知らなかったことを学ぶこと」が楽しくて始めたのだということを忘れずにいたいと思います。他のすごい開発者と比べすぎず、自分のペースで一つずつ進めていくことの大切さを、最近あらためて感じています。

---

## 📱 iOS (SwiftUI)

- Worked with Codex to define and review the core requirements for the new Chord Tone Practice mode.
- Finalized the rules for root selection, chord quality, triad patterns, and valid answers across three consecutive strings.
- Defined the behavior for temporary selections, corrections, feedback, completion, navigation, and the settings overlay.
- Reviewed and approved the Task 8 specification before beginning the Swift implementation.
- Used the results of an AI-generated JavaScript investigation to validate the proposed game rules across all 504 possible conditions.
- Added the specification, investigation report, and reusable validation script to the repository.
- I reviewed `chord-tone-practice-investigation.js`, a validation script that the AI created before implementing the new Chord Tone Practice feature in SwiftUI.
- I clarified why the AI chose to create a separate JavaScript script: it needed a quick, isolated way to test whether the proposed game rules would work across every possible combination before those rules became part of the app.
- I examined how the script generated and validated 504 cases: 12 root notes, two chord qualities, three degree patterns, and seven visible fret ranges.
- I traced the script from top to bottom, including how it calculated note names, found target positions on each string, built valid three-note answer sets, and checked whether answer sets shared fretboard positions.
- I reviewed the custom functions together with the JavaScript features used inside them, including `map()`, `filter()`, `flatMap()`, `reduce()`, `some()`, `every()`, `Set`, `Map`, and bit masks.
- I learned how to debug the script by adding breakpoints, using conditional breakpoints for a specific root, quality, pattern, and fret range, and inspecting local variables such as `sets`, `positions`, and `visibleFretStart`.
- I documented the script’s execution order, validation logic, JavaScript syntax, and results in a separate Markdown guide so that I can revisit the investigation later.

---

# 💡 Key Takeaways

## 📱 SwiftUI Learning

- I learned that AI-assisted design can include validating a proposed game mechanic before implementing it in the project’s primary development language.
- Codex independently chose JavaScript as a separate validation environment, even though the application itself is being developed in Swift and SwiftUI.
- I found it interesting that Codex reproduced the planned game logic independently in JavaScript and tested every combination before implementing the production logic.
- The investigation confirmed that the proposed rules would not create overlapping answer positions, unreachable progress totals, invalid patterns, or answer-order dead ends.
- This approach showed me that implementation risks can be identified during the design phase instead of waiting until after the Swift code and unit tests have been written.
- After the Swift game logic is implemented, I plan to write unit tests to confirm that the Swift results match the independently calculated JavaScript results.
- I learned that AI can use a small program written in a language separate from the main application to validate a design before implementing it. In this case, JavaScript was used to test the planned SwiftUI game logic without changing the iOS application.
- The script verified that every planned question had between one and three valid answer sets, with no zero-answer cases, overlapping answer positions, unreachable progress totals, order-dependent dead ends, or fret-range changes that made the current pattern unavailable.
- This validation allowed me to finalize important rules with more confidence, including using the total number of answer sets as the progress denominator, preventing the reuse of found positions, allowing answers in any order, and preserving the pattern when the fret range changes.
- I learned that reviewing AI-generated validation code is just as important as reviewing the final application code. A successful result is not enough—I need to understand what inputs were tested, how the expected conditions were defined, and what the results actually guarantee.
- I gained a clearer understanding of JavaScript’s execution flow, including how top-level code runs, when custom functions are called, how nested loops generate all test cases, and how callbacks pass values through methods such as `map()`, `filter()`, `some()`, and `every()`.
- I also learned practical debugging techniques. In particular, I found that checking only `visibleFretStart` was not enough because the same value appears under many roots, qualities, and patterns. A conditional breakpoint must include the complete test condition.
- Reviewing the script sometimes felt like being the parent of an extraordinarily gifted child: the AI produced a clever solution very quickly, while I had to slow everything down and ask exactly how it worked. Understanding the JavaScript took time, but the process gave me a valuable opportunity to learn rather than simply accepting the AI’s result.

---

# 🚀 Next Week

- Chord Tone Practice modeのUI設計を進めていく
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
