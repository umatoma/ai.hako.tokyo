---
title: "Spec Kit ドキュメントサイト トップ"
title_original: "GitHub Spec Kit | Spec Kit Documentation"
source_url: https://github.github.com/spec-kit/
captured_at: 2026-05-28
published_at: 2025-09-02
author: GitHub (github/spec-kit メンテナー)
original_language: en
tags: [spec-kit, documentation, landing-page, ecosystem]
---

> 取り込みメモ: 公式ドキュメントサイトのトップページの日本語訳。WebFetch で取得したものを翻訳。スクリーンショットやマーケティングビジュアルは省略し、テキスト構造のみ保持。コミュニティ統計の数値は取得時点 (2026-05-28)。

# GitHub Spec Kit

> 「Define what to build before building it — with any AI coding agent.」
> **構築する前に「何を作るか」を定義する — どんな AI コーディングエージェントとも組み合わせて。**

Spec Kit は Spec-Driven Development (SDD) のためのツールキットで、AI 支援ソフトウェア開発において仕様を中心に据える方法論を実装する。メソドロジーの流れ:

**Spec → Plan → Tasks → Implement**

---

## 主な特徴

### デフォルトで Spec-Driven

中核となる SDD プロセスは「リッチなテンプレート、品質チェックリスト、成果物横断分析 (cross-artifact analysis)」を提供する。各フェーズが Markdown 成果物を生成し、次のステージへ渡される。

### どんなコーディングエージェントでも使える

**30 種類の連携** — Copilot、Gemini、Codex、Windsurf、Claude、Forge、Kiro など。`specify init` コマンドでベンダーロックインなしにエージェントを切り替えられる。

### 自分仕様にする

**105 件のコミュニティ拡張**（60 人以上の作者）、**22 のプリセット**、現在も増加中。代替プロセスも利用可能:

- **AIDE** — 7 ステップの AI 駆動エンジニアリング
- **Canon** — ベースライン駆動のワークフロー
- **Product Forge** — プロダクトマネジメント指向
- **FX→.NET** — .NET Framework 移行
- **MAQA** — QA を伴うマルチエージェント協調

### 組織に取り込む

オフラインで動作、Windows / macOS / Linux 対応。**自社ホスト型の拡張・プリセットカタログ**もサポート。

---

## コミュニティ統計（取得時点: 2026-05-28）

- **106K+** GitHub スター
- **200+** コントリビューター
- **30** 連携
- **105** 拡張
- **22** プリセット

---

## クイックスタートコマンド

```
uvx --from git+https://github.com/github/spec-kit.git
specify init my-project --integration copilot
```

---

## ナビゲーション（原文ページのカテゴリ）

> 注: 原文ページにはハイパーリンクが付いている。リンク先 URL の実体まで取得できた項目だけ URL を併記する。

- Getting Started（始め方）
- Reference（リファレンス）
- Community（コミュニティ）
  - Extensions: https://github.github.io/spec-kit/community/extensions.html
  - Presets: https://github.github.io/spec-kit/community/presets.html
  - Walkthroughs: https://github.github.io/spec-kit/community/walkthroughs.html
  - Friends: https://github.github.io/spec-kit/community/friends.html
- Development（開発）
- Integrations Reference: https://github.github.io/spec-kit/reference/integrations.html
- CLI Reference: https://github.github.io/spec-kit/reference/overview.html
- Extensions Reference: https://github.github.io/spec-kit/reference/extensions.html
- Presets Reference: https://github.github.io/spec-kit/reference/presets.html
