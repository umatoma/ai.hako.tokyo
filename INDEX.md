# INDEX

このリポジトリに**現在何があるか**の一覧。CLAUDE.md が「どこに何を置くか（規約）」だとすれば、こちらは「実際に何が置いてあるか（現状）」。

新しいノートを追加・移動・削除したら、このファイルも更新する。

---

## ユースケース別（やりたいこと → 読むもの）

README.md と同じ 4 フェーズで整理（**まず始める / 判断する / 原典で確認する / このリポを育てる**）。原典セクションは下の `sources/` 一覧と重複するため省略。

### 1. まず始める（実践）

| やりたいこと | 読むもの |
|---|---|
| 新しいリポに Claude Code を導入する | [`playbooks/software-development/01-claude-codeを導入する.md`](playbooks/software-development/01-claude-codeを導入する.md) |
| `CLAUDE.md` を書く / 育てる | [`playbooks/software-development/02-claude-mdを書く.md`](playbooks/software-development/02-claude-mdを書く.md) |

### 2. 判断する（使い分け・原則）

| やりたいこと | 読むもの |
|---|---|
| Claude のサーフェス（Chat/Cowork/Code）を使い分ける | [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) |
| Claude Code の出力を HTML / Markdown で使い分ける | [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md#claude-code-出力の選び方html-vs-markdown) |
| Spec-Driven Development とは何か / 4 フェーズの流れ | [`frameworks/github-spec-kit.md`](frameworks/github-spec-kit.md) |
| 仕様駆動でコンスティチューションを使う意味 | [`frameworks/github-spec-kit.md`](frameworks/github-spec-kit.md#コンスティチューション-constitution--不変原則による規律) |
| Spec Kit を導入すべきシナリオ（0→1 / N→N+1 / レガシー） | [`frameworks/github-spec-kit.md`](frameworks/github-spec-kit.md#特に効く-3-つの場面) |
| AWS AI-DLC とは何か / 3 フェーズと Bolts | [`frameworks/aws-ai-dlc.md`](frameworks/aws-ai-dlc.md) |
| Mob Elaboration / Mob Construction とは | [`frameworks/aws-ai-dlc.md`](frameworks/aws-ai-dlc.md#1-サイクルのインタラクションパターン) |
| GSD (Get Shit Done Redux) の 6 コマンドループ | [`frameworks/open-gsd-get-shit-done-redux.md`](frameworks/open-gsd-get-shit-done-redux.md) |
| コンテキスト腐敗 (context rot) と並列波実行 | [`frameworks/open-gsd-get-shit-done-redux.md`](frameworks/open-gsd-get-shit-done-redux.md#なぜ効くか--3-つの問題と-gsd-の答え) |
| **Spec Kit / AI-DLC / GSD を使い分ける** | [`topics/software-development/ai-sdlc-methodologies-compared.md`](topics/software-development/ai-sdlc-methodologies-compared.md) |
| 3 メソドロジーの共通アンチパターン | [`topics/software-development/ai-sdlc-methodologies-compared.md`](topics/software-development/ai-sdlc-methodologies-compared.md#典型的なアンチパターン横断) |
| アイデア / MVP / Launch / Scale 段階で何を優先するか | [`topics/software-development/ai-native-startup-lifecycle.md`](topics/software-development/ai-native-startup-lifecycle.md) |
| スコープクリープを防ぐ | [`topics/software-development/ai-native-startup-lifecycle.md`](topics/software-development/ai-native-startup-lifecycle.md) MVP 章 ＋ [`playbooks/software-development/01-claude-codeを導入する.md`](playbooks/software-development/01-claude-codeを導入する.md) ステップ 3 |
| エージェント時代の検証・確証バイアス対策 | [`topics/software-development/ai-native-startup-lifecycle.md`](topics/software-development/ai-native-startup-lifecycle.md) Idea 章 ＋ [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) の「やってはいけないこと」 |

### 3. このリポを育てる（貢献）

| やりたいこと | 読むもの |
|---|---|
| 新しい記事・PDF をこのリポに取り込む | [`playbooks/knowledge-base/01-外部情報を取り込む.md`](playbooks/knowledge-base/01-外部情報を取り込む.md) |

---

## sources/ — 一次情報（日本語訳）

### Anthropic

#### ブログ

- [`2026-05-14 The Founder's Playbook: AI ネイティブなスタートアップを作る`](sources/anthropic/blog/2026-05-14-the-founders-playbook.md) — 同名 PDF への入口記事
- [`2026-05-20 Claude Code を使う: HTML の不合理なまでの有効性`](sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md) — Markdown より HTML を成果物形式として好む理由・ユースケース

#### ドキュメント・ホワイトペーパー

- [`The Founder's Playbook (PDF 全 36 ページ Markdown 変換版)`](sources/anthropic/docs/the-founders-playbook.md) — Idea / MVP / Launch / Scale の 4 段階モデルと AI 活用

### Google

（未取り込み）

- 想定: `sources/google/` に Gemini / NotebookLM / NanoBanana 関連を追加予定

### GitHub

#### spec-kit

- [`readme.md`](sources/github/spec-kit/readme.md) — 公式リポジトリ README。CLI コマンド、4 フェーズ、Extensions/Presets、9 条項、詳細プロセス（Taskify 例）
- [`spec-driven.md`](sources/github/spec-kit/spec-driven.md) — SDD の哲学・ワークフロー・コンスティチューション 9 条項・テンプレートが LLM を制約する仕組み（中核ドキュメント）
- [`docs-home.md`](sources/github/spec-kit/docs-home.md) — 公式ドキュメントサイトのトップ。コミュニティ統計と代替プロセス (AIDE/Canon/Product Forge/...)
- [`installation.md`](sources/github/spec-kit/installation.md) — インストール手順（uv / pipx / Shell vs PowerShell / Air-Gapped）
- [`2025-09-02-spec-driven-development-announcement.md`](sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md) — GitHub Blog 発表記事（"intent is the source of truth"）

### AWS

#### ai-dlc

- [`2025-07-31-ai-driven-development-life-cycle.md`](sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md) — AWS DevOps Blog 発表記事。AI-DLC の 2 つの設計次元、3 フェーズ、Mob Elaboration/Construction、Bolts/Units of Work
- [`2025-11-29-open-sourcing-adaptive-workflows.md`](sources/aws/ai-dlc/2025-11-29-open-sourcing-adaptive-workflows.md) — OSS 化ブログ。3 つの解こうとする課題（画一性・深さ欠如・過剰自動化）と Workflow Scaffolds
- [`2025-11-29-building-with-ai-dlc-using-amazon-q-developer.md`](sources/aws/ai-dlc/2025-11-29-building-with-ai-dlc-using-amazon-q-developer.md) — Amazon Q Developer で川渡りパズルを作るウォークスルー。`aidlc-docs/` の生成成果物が一望できる
- [`aidlc-workflows-readme.md`](sources/aws/ai-dlc/aidlc-workflows-readme.md) — 公式リポジトリ README。プラットフォーム別セットアップ（Kiro/Q/Cursor/Cline/Claude Code/Copilot/Codex）、信条 5 つ、Extensions 仕組み、補助ツール

### open-gsd

#### get-shit-done-redux

- [`readme.md`](sources/open-gsd/get-shit-done-redux/readme.md) — 公式リポジトリ README。6 コマンドループ（Init/Discuss/Plan/Execute/Verify/Ship）、コンテキスト腐敗対策、並列波実行、`.planning/` 永続成果物、15 ランタイム互換性、open-gsd への移行経緯

### Dify

（未取り込み）

- 想定: `sources/dify/` に Dify 関連ドキュメント・ブログを追加予定

### n8n

（未取り込み）

- 想定: `sources/n8n/` に n8n 関連ドキュメント・ブログを追加予定

---

## frameworks/ — ベンダー/ツール別の整理ノート

- [`anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) — Chat / Claude Cowork / Claude Code のサーフェス選択、HTML 出力の指針、CLAUDE.md 運用のお作法
- [`github-spec-kit.md`](frameworks/github-spec-kit.md) — Spec-Driven Development の 4 フェーズ (Spec→Plan→Tasks→Implement)、コンスティチューション 9 条項、Extensions/Presets、適用シナリオ
- [`aws-ai-dlc.md`](frameworks/aws-ai-dlc.md) — AI-Driven Development Life Cycle の 3 フェーズ（Inception/Construction/Operations）、Mob Elaboration/Construction、Workflow Scaffolds、信条 5 つ
- [`open-gsd-get-shit-done-redux.md`](frameworks/open-gsd-get-shit-done-redux.md) — GSD の 6 コマンドループ、コンテキスト腐敗対策、並列波実行、`.planning/` 永続成果物

> 3 メソドロジーの横断比較は [`topics/software-development/ai-sdlc-methodologies-compared.md`](topics/software-development/ai-sdlc-methodologies-compared.md) に集約してある。

---

## topics/ — 業務領域別のベンダー横断ノート

### software-development/

- [`ai-native-startup-lifecycle.md`](topics/software-development/ai-native-startup-lifecycle.md) — 4 段階モデル（Idea/MVP/Launch/Scale）の俯瞰。現状は Anthropic 単一視点
- [`ai-sdlc-methodologies-compared.md`](topics/software-development/ai-sdlc-methodologies-compared.md) — Spec Kit / AWS AI-DLC / GSD の横断比較。中心概念・フェーズ構造・規律強制・協業様式・並列実行・対象規模など、使い分けの目安まで

### design / marketing / sales / hr / cross

（コンテンツ未追加 / 各ディレクトリの README で扱う範囲を明示）

---

## playbooks/ — 業務領域別の実践手順

### software-development/

- [`01-claude-codeを導入する.md`](playbooks/software-development/01-claude-codeを導入する.md) — Claude Code を新規・既存リポに導入するときの初期セットアップ手順
- [`02-claude-mdを書く.md`](playbooks/software-development/02-claude-mdを書く.md) — `CLAUDE.md` の書き方・育て方・アンチパターン

### knowledge-base/ — このリポ自体の運用

- [`01-外部情報を取り込む.md`](playbooks/knowledge-base/01-外部情報を取り込む.md) — ブログ・PDF を `sources/` に取り込む手順とチェックリスト

### design / marketing / sales / hr

（コンテンツ未追加 / 各ディレクトリの README に想定例を記載）

---

## _templates/ — テンプレート

- [`source-blog.md`](_templates/source-blog.md) — ブログ記事取り込み用
- [`source-pdf.md`](_templates/source-pdf.md) — PDF 取り込み用
- [`framework-or-topic.md`](_templates/framework-or-topic.md) — 二次情報ノート用

---

## 規約・運用

- [`README.md`](README.md) — 訪問者向け入口（やりたいこと別のリンク集）
- [`CLAUDE.md`](CLAUDE.md) — 編集者（人 / Claude Code）向けの規約: ディレクトリ役割、frontmatter、PDF 取り扱い、言語ポリシー

---

## 統計（参考）

- 一次情報: 13 件（Anthropic ブログ 2 / PDF 1、GitHub spec-kit 5、AWS ai-dlc 4、open-gsd 1）
- 二次情報: 6 件（frameworks 4 / topics 2）
- プレイブック: 3 件（software-development 2 / knowledge-base 1）
- 業務領域: software-development が稼働、design/marketing/sales/hr/cross は枠のみ
- ベンダー/ツール: Anthropic / GitHub (spec-kit) / AWS (ai-dlc) / open-gsd (GSD) が稼働、Google/Dify/n8n は枠のみ
