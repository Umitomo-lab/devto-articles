---
title: Dev.to自動投稿の初回テスト
published: false
description: GitHub Actionsからdev-to-gitで同期する初回テスト記事です
tags: nodejs, githubactions, devto
series:
canonical_url:
---

<!--
【MEMO】

■ 記事IDの取得
Dev.toの記事ページのWeb開発画面のコンソールで以下を実行
$('div[data-article-id]').getAttribute('data-article-id')

■ カバーイメージ
Front Matter に追加する
cover_image: https://raw.githubusercontent.com/{ユーザー}/{リポジトリ}/{ブランチ}/{パス}

■ 画像の配置
assets フォルダに格納して相対パスで指定
例: ./assets/image.png

■ 参考
https://github.com/maxime1992/dev.to
-->

# Dev.to自動投稿の初回テスト

これは GitHub 管理の記事を Dev.to に同期するためのテストです。

- Markdown で管理
- GitHub Actions で実行
- dev-to-git で Dev.to に反映
