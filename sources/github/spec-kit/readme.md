---
title: "Spec Kit README (公式リポジトリ)"
title_original: "Spec Kit — Toolkit to help you get started with Spec-Driven Development"
source_url: https://github.com/github/spec-kit
captured_at: 2026-05-28
published_at: 2025-09-02
author: GitHub (github/spec-kit メンテナー)
original_language: en
tags: [spec-kit, spec-driven-development, github, cli, ai-coding-agents]
---

> 取り込みメモ: 公式リポジトリの README（最新リリース v0.8.16 / 2026-05-27 時点）の日本語訳。WebFetch で取得した Markdown を翻訳。コードブロック・コマンド・パス・絵文字は原文のまま残している。本文は継続的に更新されるため、最新版は `source_url` を参照。

# 🌱 Spec Kit

### _高品質なソフトウェアを、より速く作る。_

**プロダクトのシナリオと予測可能な成果に集中できるようにする、オープンソースのツールキット。すべてのコードを「vibe coding（雰囲気コーディング）」でゼロから書く必要はありません。**

---

## 目次

- [🤔 Spec-Driven Development とは？](#-spec-driven-development-とは)
- [⚡ はじめる](#-はじめる)
- [📽️ ビデオ概説](#-ビデオ概説)
- [🧩 コミュニティ拡張 (Community Extensions)](#-コミュニティ拡張-community-extensions)
- [🎨 コミュニティプリセット (Community Presets)](#-コミュニティプリセット-community-presets)
- [🚶 コミュニティウォークスルー](#-コミュニティウォークスルー)
- [🛠️ コミュニティフレンド](#-コミュニティフレンド)
- [🤖 サポートされる AI コーディングエージェント連携](#-サポートされる-ai-コーディングエージェント連携)
- [🔧 Specify CLI リファレンス](#-specify-cli-リファレンス)
- [🧩 Spec Kit を自分仕様にする: 拡張とプリセット](#-spec-kit-を自分仕様にする-拡張とプリセット)
- [📚 中核となる哲学](#-中核となる哲学)
- [🌟 開発フェーズ](#-開発フェーズ)
- [🎯 実験的なゴール](#-実験的なゴール)
- [🔧 前提条件](#-前提条件)
- [📖 さらに学ぶ](#-さらに学ぶ)
- [📋 詳細プロセス](#-詳細プロセス)
- [💬 サポート](#-サポート)
- [🙏 謝辞](#-謝辞)
- [📄 ライセンス](#-ライセンス)

---

## 🤔 Spec-Driven Development とは？

Spec-Driven Development（仕様駆動開発）は、従来のソフトウェア開発の**力関係をひっくり返す**。何十年もの間、コードこそが王だった ― 仕様 (specifications) は単なる足場であり、「本物の仕事」であるコーディングが始まったら捨てられるものだった。Spec-Driven Development はこれを変える: **仕様が実行可能 (executable) になり**、実装の指針となるだけでなく、動作する実装そのものを直接生成する。

---

## ⚡ はじめる

### 1. Specify CLI をインストールする

**[uv](https://docs.astral.sh/uv/)** が必要（[uv のインストール手順](https://github.com/github/spec-kit/blob/main/docs/install/uv.md)）。`vX.Y.Z` を [Releases](https://github.com/github/spec-kit/releases) の最新タグに置き換える:

```
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z
```

別のインストール方法・検証・アップグレード・トラブルシュートは [Installation Guide](https://github.com/github/spec-kit/blob/main/docs/installation.md) を参照。

### 2. プロジェクトを初期化する

```
specify init my-project --integration copilot
cd my-project
```

### 3. プロジェクトの原則 (principles) を確立する

プロジェクトディレクトリでコーディングエージェントを起動する。ほとんどのエージェントは spec-kit を `/speckit.*` スラッシュコマンドとして公開する。Codex CLI の skills モードでは `$speckit-*` を使う。

**`/speckit.constitution`** コマンドで、プロジェクトの統治原則 (governing principles) と開発ガイドラインを作成する。これが以降のすべての開発の指針となる。

```
/speckit.constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements
```

### 4. 仕様 (spec) を作る

**`/speckit.specify`** コマンドで、作りたいものを記述する。**何 (what) を、なぜ (why)** に焦点を当てる。技術スタックには触れない。

```
/speckit.specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums. Within each album, photos are previewed in a tile-like interface.
```

### 5. 技術実装計画を作る

**`/speckit.plan`** コマンドで、技術スタックとアーキテクチャの選択を伝える。

```
/speckit.plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.
```

### 6. タスクに分解する

**`/speckit.tasks`** で、実装計画から実行可能なタスクリストを生成する。

```
/speckit.tasks
```

### 7. 実装を実行する

**`/speckit.implement`** で、計画に沿ってすべてのタスクを実行し、機能を作り込む。

```
/speckit.implement
```

詳細な手順は [包括的なガイド](https://github.com/github/spec-kit/blob/main/spec-driven.md) を参照。

---

## 📽️ ビデオ概説

Spec Kit の動作を見たい場合は [ビデオ概説](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv) を視聴。

---

## 🧩 コミュニティ拡張 (Community Extensions)

コミュニティが投稿した拡張 (extensions) は、Spec Kit に新しいコマンド・フック・機能を追加する。全リストは [Community Extensions](https://github.github.io/spec-kit/community/extensions.html) ページを参照。

> **Note**
> コミュニティ拡張は各作者が独立して作成・保守しており、メンテナーはカタログエントリーの形式が完全かつ正しいかだけを確認している。**拡張のコード自体をレビュー・監査・推奨・サポートはしない**。インストール前にソースコードを確認し、自己責任で利用すること。

自分の拡張を投稿するには [Extension Publishing Guide](https://github.com/github/spec-kit/blob/main/extensions/EXTENSION-PUBLISHING-GUIDE.md) を参照。

---

## 🎨 コミュニティプリセット (Community Presets)

コミュニティが投稿したプリセット (presets) は、ツール自体を変更せずに Spec Kit の振る舞い（テンプレート・コマンド・用語）を上書きしてカスタマイズする。全リストは [Community Presets](https://github.github.io/spec-kit/community/presets.html) ページを参照。

> **Note**
> コミュニティプリセットはサードパーティの貢献であり、Spec Kit チームは保守していない。使用前に注意深く確認すること。免責事項の全文は上記ドキュメントを参照。

自分のプリセットを投稿するには [Presets Publishing Guide](https://github.com/github/spec-kit/blob/main/presets/PUBLISHING.md) を参照。

---

## 🚶 コミュニティウォークスルー

異なるシナリオでの Spec-Driven Development の実例を、コミュニティが投稿したウォークスルーで見ることができる。全リストは [Community Walkthroughs](https://github.github.io/spec-kit/community/walkthroughs.html) ページを参照。

---

## 🛠️ コミュニティフレンド

Spec Kit を拡張・可視化・基盤として使うコミュニティプロジェクト。全リストは [Community Friends](https://github.github.io/spec-kit/community/friends.html) ページを参照。

---

## 🤖 サポートされる AI コーディングエージェント連携

Spec Kit は **30 以上の AI コーディングエージェント**（CLI ツールと IDE ベースのアシスタントの両方）で動作する。注釈と使い方を含む全リストは [Supported AI Coding Agent Integrations](https://github.github.io/spec-kit/reference/integrations.html) ガイドを参照。

インストール済みバージョンで利用可能なすべての連携を見るには `specify integration list` を実行する。

### 利用可能なスラッシュコマンド

`specify init` 実行後、AI コーディングエージェントは構造化された開発のための以下のスラッシュコマンドを使えるようになる。Skills モードをサポートする連携では、`--integration <agent> --integration-options="--skills"` を渡すことで、スラッシュコマンドのプロンプトファイルではなくエージェントスキルがインストールされる。

#### コアコマンド

Spec-Driven Development ワークフローの必須コマンド:

| コマンド | エージェントスキル | 説明 |
|---|---|---|
| `/speckit.constitution` | `speckit-constitution` | プロジェクトの統治原則と開発ガイドラインを作成・更新 |
| `/speckit.specify` | `speckit-specify` | 作るものを定義する（要件とユーザーストーリー） |
| `/speckit.plan` | `speckit-plan` | 選択した技術スタックでの技術実装計画を作る |
| `/speckit.tasks` | `speckit-tasks` | 実装用の実行可能なタスクリストを生成 |
| `/speckit.taskstoissues` | `speckit-taskstoissues` | 生成されたタスクリストを GitHub Issue に変換し、追跡と実行に使う |
| `/speckit.implement` | `speckit-implement` | 計画に従って全タスクを実行し、機能を構築 |

#### オプションコマンド

品質と検証を強化する追加コマンド:

| コマンド | エージェントスキル | 説明 |
|---|---|---|
| `/speckit.clarify` | `speckit-clarify` | 仕様の曖昧な箇所を明確化する（`/speckit.plan` の前に推奨。旧 `/quizme`） |
| `/speckit.analyze` | `speckit-analyze` | 成果物横断 (cross-artifact) の一貫性とカバレッジ分析（`/speckit.tasks` の後、`/speckit.implement` の前に実行） |
| `/speckit.checklist` | `speckit-checklist` | 要件の完全性・明瞭さ・一貫性を検証するカスタム品質チェックリストを生成（「英語の単体テスト」のようなもの） |

---

## 🔧 Specify CLI リファレンス

全コマンドの詳細・オプション・例は [CLI Reference](https://github.github.io/spec-kit/reference/overview.html) を参照。

---

## 🧩 Spec Kit を自分仕様にする: 拡張とプリセット

Spec Kit は 2 つの補完的なシステム（**拡張 (extensions)** と **プリセット (presets)**）に加え、一時的な調整のためのプロジェクトローカル上書きを通じて、ニーズに合わせて調整できる:

| 優先度 | コンポーネント種別 | 場所 |
|---|---|---|
| ⬆ 1 | プロジェクトローカル上書き | `.specify/templates/overrides/` |
| 2 | プリセット — コアと拡張をカスタマイズ | `.specify/presets/templates/` |
| 3 | 拡張 — 新しい機能を追加 | `.specify/extensions/templates/` |
| ⬇ 4 | Spec Kit Core — 組み込みの SDD コマンドとテンプレート | `.specify/templates/` |

- **テンプレート**は**実行時**に解決される — Spec Kit はスタックを上から下へたどり、最初にマッチしたものを使う。
- プロジェクトローカル上書き (`.specify/templates/overrides/`) は、フルなプリセットを作らずに 1 プロジェクト限定の調整を加えるためのもの。
- **拡張・プリセットのコマンド**は**インストール時**に適用される — `specify extension add` や `specify preset add` を実行すると、コマンドファイルがエージェントディレクトリ（例: `.claude/commands/`）に書き込まれる。
- 複数のプリセットや拡張が同じコマンドを提供する場合、優先度の高いものが勝つ。削除時は、次に優先度の高いものが自動的に復元される。
- 上書きやカスタマイズが何もなければ、Spec Kit はコアのデフォルトを使う。

### 拡張 (Extensions) — 新しい機能を追加

**拡張**は、Spec Kit のコアを超える機能が必要なときに使う。新しいコマンドとテンプレートを導入する — 例: 組み込みの SDD コマンドではカバーされないドメイン固有のワークフロー、外部ツール連携、新しい開発フェーズの追加。「Spec Kit に何ができるか」を広げる。

```
# 利用可能な拡張を検索
specify extension search

# 拡張をインストール
specify extension add <extension-name>
```

例えば拡張で Jira 連携、実装後のコードレビュー、V-Model のテストトレーサビリティ、プロジェクト健全性診断などを追加できる。

詳細は [Extensions reference](https://github.github.io/spec-kit/reference/extensions.html) を参照。何があるかは上記の[コミュニティ拡張](#-コミュニティ拡張-community-extensions)を参照。

### プリセット (Presets) — 既存ワークフローをカスタマイズ

**プリセット**は、新しい機能を加えずに「Spec Kit の動き方」を変えたいときに使う。コアおよびインストール済み拡張に同梱されるテンプレートやコマンドを上書きする — 例: コンプライアンス指向の仕様フォーマットを強制する、ドメイン固有の用語を使う、計画とタスクに組織標準を適用する。Spec Kit とその拡張が生み出す成果物・指示をカスタマイズする。

```
# 利用可能なプリセットを検索
specify preset search

# プリセットをインストール
specify preset add <preset-name>
```

例えばプリセットで、規制対応のトレーサビリティを要求する仕様テンプレートに再構成する、使用しているメソドロジー（Agile、Kanban、Waterfall、Jobs-to-be-Done、ドメイン駆動設計）に合わせる、計画に必須のセキュリティレビュー関門 (gate) を加える、タスク順序をテストファーストにする、ワークフロー全体を別言語にローカライズする、といった調整が可能。[pirate-speak デモ](https://github.com/mnriem/spec-kit-pirate-speak-preset-demo) はカスタマイズの深さの一例。複数のプリセットを優先度を付けて重ねることもできる。

詳細（解決順序と優先度スタッキングを含む）は [Presets reference](https://github.github.io/spec-kit/reference/presets.html) を参照。

### どちらを使うか

| ゴール | 使うもの |
|---|---|
| 新しいコマンドやワークフローを追加 | 拡張 |
| 仕様・計画・タスクのフォーマットをカスタマイズ | プリセット |
| 外部ツール・サービスと連携 | 拡張 |
| 組織標準・規制標準を強制 | プリセット |
| 再利用可能なドメイン固有テンプレートを配布 | どちらでも — テンプレート上書きならプリセット、新コマンド込みのテンプレートなら拡張 |

---

## 📚 中核となる哲学

Spec-Driven Development は、次の点を重視する構造化されたプロセス:

- **意図駆動開発 (Intent-driven development)** — 仕様が「_どうやって_」より先に「_何を_」を定義する
- **リッチな仕様作成** — ガードレールと組織原則を活用
- **多段階の洗練** — プロンプトから一発でコード生成するのではなく、段階的に磨き上げる
- **AI モデルの高度な能力への強い依存** — 仕様の解釈を担わせる

---

## 🌟 開発フェーズ

| フェーズ | 焦点 | 主な活動 |
|---|---|---|
| **0-to-1 Development**（「グリーンフィールド」） | ゼロから生成 | - 高レベル要件から開始<br>- 仕様を生成<br>- 実装ステップを計画<br>- 本番運用可能なアプリを構築 |
| **Creative Exploration**（創造的探索） | 並行実装 | - 多様な解を探索<br>- 複数の技術スタック・アーキテクチャをサポート<br>- UX パターンを実験 |
| **Iterative Enhancement**（反復強化、「ブラウンフィールド」） | レガシー近代化 | - 機能を反復的に追加<br>- レガシーシステムをモダン化<br>- プロセスを適応 |

---

## 🎯 実験的なゴール

研究と実験の焦点は次の通り:

### 技術独立性

- 多様な技術スタックでアプリを作る
- 「Spec-Driven Development は特定の技術・言語・フレームワークに縛られないプロセスである」という仮説を検証

### エンタープライズ制約

- ミッションクリティカルなアプリ開発を実証
- 組織的制約（クラウド事業者、技術スタック、エンジニアリングプラクティス）を取り込む
- エンタープライズのデザインシステムとコンプライアンス要件をサポート

### ユーザー中心の開発

- 異なるユーザーコホート・好みに向けたアプリを構築
- 多様な開発アプローチ（vibe-coding から AI ネイティブ開発まで）をサポート

### 創造的・反復的プロセス

- 並行実装探索のコンセプトを検証
- 堅牢な反復的機能開発ワークフローを提供
- アップグレード・近代化タスクを扱えるようプロセスを拡張

---

## 🔧 前提条件

- **Linux/macOS/Windows**
- [サポート対象](#-サポートされる-ai-コーディングエージェント連携)の AI コーディングエージェント
- パッケージ管理は [uv](https://docs.astral.sh/uv/) を推奨。永続インストールには [pipx](https://pipx.pypa.io/) も可
- [Python 3.11+](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)

特定のエージェントで問題が起きたら、Issue を開いて連携の精度を上げられるようにしてほしい。

---

## 📖 さらに学ぶ

- **[Spec-Driven Development の完全なメソドロジー](https://github.com/github/spec-kit/blob/main/spec-driven.md)** — 全プロセスの深堀り
- **[詳細ウォークスルー](#-詳細プロセス)** — ステップごとの実装ガイド

---

## 📋 詳細プロセス

### プロジェクトのブートストラップ

Specify CLI でプロジェクトをブートストラップすると、必要な成果物が環境に取り込まれる。実行:

```
specify init <project_name>
```

カレントディレクトリで初期化する場合:

```
specify init .
# または --here フラグ
specify init --here
# 既にファイルがあるディレクトリで確認をスキップ
specify init . --force
# または
specify init --here --force
```

対話型ターミナルでは、使っているコーディングエージェント連携を選ぶよう促される。CI などの非対話セッションでは、`--integration` を渡さない限り `specify init` は GitHub Copilot をデフォルトとする。事前に連携を指定することもできる:

```
specify init <project_name> --integration copilot
specify init <project_name> --integration gemini
specify init <project_name> --integration codex

# またはカレントディレクトリで:
specify init . --integration copilot
specify init . --integration codex --integration-options="\--skills"

# または --here フラグで
specify init --here --integration copilot
specify init --here --integration codex --integration-options="\--skills"

# 空でないカレントディレクトリへ強制マージ
specify init . --force --integration copilot

# または
specify init --here --force --integration copilot
```

CLI は Claude Code / Gemini CLI / Cursor CLI / Qwen CLI / opencode / Codex CLI / Qoder CLI / Tabnine CLI / Kiro CLI / Pi / Forge / Goose / Mistral Vibe がインストールされているか確認する。インストールされていない場合、あるいは適切なツール確認なしでテンプレートを取得したい場合は `--ignore-agent-tools` を付ける:

```
specify init <project_name> --integration copilot --ignore-agent-tools
```

### **STEP 1:** プロジェクト原則を確立する

プロジェクトフォルダに移動し、コーディングエージェントを起動する。例では `claude` を使う。

`/speckit.constitution`、`/speckit.specify`、`/speckit.plan`、`/speckit.tasks`、`/speckit.implement` の各コマンドが見えれば、正しく設定されている。

最初のステップは `/speckit.constitution` でプロジェクトの統治原則を確立すること。これにより、以降のすべての開発フェーズで意思決定が一貫する:

```
/speckit.constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements. Include governance for how these principles should guide technical decisions and implementation choices.
```

このステップで `.specify/memory/constitution.md` が作成・更新され、コーディングエージェントが仕様作成・計画・実装の各フェーズで参照する基本ガイドラインが入る。

### **STEP 2:** プロジェクト仕様を作る

原則ができたら、機能仕様を作る。`/speckit.specify` コマンドを使い、開発したいプロジェクトの具体的な要件を伝える。

> **⚠️ 重要**: **何 (what) を、なぜ (why)** 作るのかを可能な限り明示する。**この時点では技術スタックに焦点を当てない**。

プロンプト例:

```
Develop Taskify, a team productivity platform. It should allow users to create projects, add team members,
assign tasks, comment and move tasks between boards in Kanban style. In this initial phase for this feature,
let's call it "Create Taskify," let's have multiple users but the users will be declared ahead of time, predefined.
I want five users in two different categories, one product manager and four engineers. Let's create three
different sample projects. Let's have the standard Kanban columns for the status of each task, such as "To Do,"
"In Progress," "In Review," and "Done." There will be no login for this application as this is just the very
first testing thing to ensure that our basic features are set up. For each task in the UI for a task card,
you should be able to change the current status of the task between the different columns in the Kanban work board.
You should be able to leave an unlimited number of comments for a particular card. You should be able to, from that task
card, assign one of the valid users. When you first launch Taskify, it's going to give you a list of the five users to pick
from. There will be no password required. When you click on a user, you go into the main view, which displays the list of
projects. When you click on a project, you open the Kanban board for that project. You're going to see the columns.
You'll be able to drag and drop cards back and forth between different columns. You will see any cards that are
assigned to you, the currently logged in user, in a different color from all the other ones, so you can quickly
see yours. You can edit any comments that you make, but you can't edit comments that other people made. You can
delete any comments that you made, but you can't delete comments anybody else made.
```

このプロンプトを入れると、Claude Code が計画と仕様ドラフトのプロセスを開始する。組み込みスクリプトを使ってリポジトリのセットアップもする。

このステップ完了時には、新しいブランチ（例: `001-create-taskify`）と新しい仕様ファイルが `specs/001-create-taskify` ディレクトリに作られている。

生成された仕様には、テンプレート通りのユーザーストーリーと機能要件が含まれる。

この時点でのプロジェクトフォルダはおおむね次の通り:

```
.
├── .specify
│   ├── memory
│   │   └── constitution.md
│   ├── scripts
│   │   └── bash
│   │       ├── check-prerequisites.sh
│   │       ├── common.sh
│   │       ├── create-new-feature.sh
│   │       ├── setup-plan.sh
│   │       └── setup-tasks.sh
│   └── templates
│       ├── plan-template.md
│       ├── spec-template.md
│       └── tasks-template.md
└── specs
    └── 001-create-taskify
        └── spec.md
```

### **STEP 3:** 機能仕様の明確化（計画前に必須）

ベースライン仕様ができたら、初回で正しく取れなかった要件を明確化する。

計画作成の**前**に構造化された明確化ワークフローを実行することで、後段の手戻りを減らせる。

推奨順序:

1. `/speckit.clarify`（構造化） — 逐次的・カバレッジベースの質問を行い、回答を「Clarifications」セクションに記録する。
2. 必要なら、さらに自由形式のリファインメントを行う。

意図的に明確化をスキップしたい場合（スパイクや探索プロトタイプ等）は、明確化が欠けていることでエージェントが止まらないよう明示的に宣言する。

`/speckit.clarify` の後でなお曖昧さが残っている場合の自由形式プロンプト例:

```
For each sample project or project that you create there should be a variable number of tasks between 5 and 15
tasks for each one randomly distributed into different states of completion. Make sure that there's at least
one task in each stage of completion.
```

Claude Code に **Review & Acceptance Checklist** を検証させることも推奨。次のプロンプトが使える:

```
Read the review and acceptance checklist, and check off each item in the checklist if the feature spec meets the criteria. Leave it empty if it does not.
```

Claude Code とのやり取りを、仕様の明確化・質問の機会として活かすことが重要 — **最初の出力を最終版扱いしないこと**。

### **STEP 4:** 計画を生成する

ここで初めて技術スタックや技術要件を具体的に指定する。プロジェクトテンプレートに組み込まれた `/speckit.plan` コマンドを以下のようなプロンプトで使う:

```
We are going to generate this using .NET Aspire, using Postgres as the database. The frontend should use
Blazor server with drag-and-drop task boards, real-time updates. There should be a REST API created with a projects API,
tasks API, and a notifications API.
```

このステップの出力には複数の実装詳細ドキュメントが含まれ、ディレクトリは次のようになる:

```
.
├── CLAUDE.md
├── .specify
│   ├── memory
│   │   └── constitution.md
│   ├── scripts
│   │   └── bash
│   │       ├── check-prerequisites.sh
│   │       ├── common.sh
│   │       ├── create-new-feature.sh
│   │       ├── setup-plan.sh
│   │       └── setup-tasks.sh
│   └── templates
│       ├── CLAUDE-template.md
│       ├── plan-template.md
│       ├── spec-template.md
│       └── tasks-template.md
└── specs
    └── 001-create-taskify
        ├── contracts
        │   ├── api-spec.json
        │   └── signalr-spec.md
        ├── data-model.md
        ├── plan.md
        ├── quickstart.md
        ├── research.md
        └── spec.md
```

`research.md` を確認し、指示通りの技術スタックが使われているかを見る。引っかかる構成要素があれば Claude Code に洗練を依頼するか、使いたいプラットフォーム/フレームワークのローカルバージョンを確認させる（例: .NET）。

加えて、変化の速い技術スタック（.NET Aspire、JS フレームワーク等）の場合は次のようなプロンプトで詳細をリサーチさせるとよい:

```
I want you to go through the implementation plan and implementation details, looking for areas that could
benefit from additional research as .NET Aspire is a rapidly changing library. For those areas that you identify that
require further research, I want you to update the research document with additional details about the specific
versions that we are going to be using in this Taskify application and spawn parallel research tasks to clarify
any details using research from the web.
```

途中で Claude Code が見当違いのリサーチに固執するようなら、次のように軌道修正する:

```
I think we need to break this down into a series of steps. First, identify a list of tasks
that you would need to do during implementation that you're not sure of or would benefit
from further research. Write down a list of those tasks. And then for each one of these tasks,
I want you to spin up a separate research task so that the net results is we are researching
all of those very specific tasks in parallel. What I saw you doing was it looks like you were
researching .NET Aspire in general and I don't think that's gonna do much for us in this case.
That's way too untargeted research. The research needs to help you solve a specific targeted question.
```

> **ℹ️ 注**: Claude Code は頼んでもいないコンポーネントを足してくることがある。理由とソースを聞き返すこと。

### **STEP 5:** 計画を Claude Code に検証させる

計画ができたら、抜け漏れがないか Claude Code に通して確認させる。次のようなプロンプトを使う:

```
Now I want you to go and audit the implementation plan and the implementation detail files.
Read through it with an eye on determining whether or not there is a sequence of tasks that you need
to be doing that are obvious from reading this. Because I don't know if there's enough here. For example,
when I look at the core implementation, it would be useful to reference the appropriate places in the implementation
details where it can find the information as it walks through each step in the core implementation or in the refinement.
```

これにより実装計画が洗練され、計画フェーズで Claude Code が見落としたかもしれない盲点を回避できる。最初のリファインメントが終わったら、実装に入る前にもう一度チェックリストを通させる。

[GitHub CLI](https://docs.github.com/en/github-cli/github-cli) がインストールされていれば、Claude Code に現在ブランチから `main` への詳細な説明付き Pull Request を作らせて、作業を可視化することもできる。

> **ℹ️ 注**: エージェントに実装させる前に、過剰設計 (over-engineering) の有無も確認するとよい（先述の通り、過剰に張り切る傾向がある）。過剰なコンポーネントや判断があれば修正を依頼する。計画策定時に `.specify/memory/constitution.md` を必ず順守することを確認する。

### **STEP 6:** /speckit.tasks でタスク分解を生成する

実装計画の検証ができたら、計画を具体的で実行可能なタスクに正しい順序で分解する。`/speckit.tasks` を使うと、実装計画から詳細なタスク分解が自動生成される:

```
/speckit.tasks
```

このステップで、機能仕様ディレクトリに `tasks.md` が作られる:

- **ユーザーストーリーごとに整理されたタスク分解** — 各ユーザーストーリーが独自のタスク群を持つ実装フェーズになる
- **依存関係管理** — コンポーネント間の依存（例: モデル → サービス → エンドポイント）を尊重した順序付け
- **並行実行マーカー** — 並行可能なタスクは `[P]` でマーキングされ、開発フローを最適化
- **ファイルパス指定** — 各タスクに実装すべき正確なファイルパスを含む
- **テスト駆動開発構造** — テスト要求があれば、テストタスクを含め、実装より前に書く順序にする
- **チェックポイント検証** — 各ユーザーストーリーフェーズに、独立動作を検証するチェックポイントを含む

生成された tasks.md は `/speckit.implement` の明確なロードマップとなり、コード品質を保ちつつユーザーストーリーを段階的に提供できる。

### **STEP 7:** 実装

準備ができたら `/speckit.implement` で実装計画を実行する:

```
/speckit.implement
```

`/speckit.implement` は以下を行う:

- すべての前提条件（constitution, spec, plan, tasks）が揃っていることを検証
- `tasks.md` からタスク分解をパース
- 依存関係と並行実行マーカーを尊重した順序でタスクを実行
- タスク計画で定義された TDD アプローチに従う
- 進捗を通知し、エラーを適切に処理

> **⚠️ 重要**: コーディングエージェントは `dotnet`、`npm` などのローカル CLI コマンドを実行する — 必要なツールがインストールされていることを確認。

実装完了後はアプリをテストし、CLI ログには出ない実行時エラー（ブラウザコンソールエラー等）を確認する。そのようなエラーはコーディングエージェントに貼り戻して解決させる。

---

## 💬 サポート

サポートが必要なときは [GitHub issue](https://github.com/github/spec-kit/issues/new) を開く。バグレポート、機能リクエスト、Spec-Driven Development の使い方に関する質問を歓迎。

---

## 🙏 謝辞

このプロジェクトは [John Lam](https://github.com/jflam) の研究と取り組みから強く影響を受けている。

---

## 📄 ライセンス

MIT オープンソースライセンス。詳細は [LICENSE](https://github.com/github/spec-kit/blob/main/LICENSE) を参照。

---

## 関連ドキュメント URL（原文末尾より）

- https://github.com/github/spec-kit/blob/main/docs/install/uv.md
- https://docs.astral.sh/uv/
- https://github.com/github/spec-kit/blob/main/docs/installation.md
- https://github.com/github/spec-kit/blob/main/spec-driven.md
- https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv
- https://github.github.io/spec-kit/community/extensions.html
- https://github.com/github/spec-kit/blob/main/extensions/EXTENSION-PUBLISHING-GUIDE.md
- https://github.github.io/spec-kit/community/presets.html
- https://github.com/github/spec-kit/blob/main/presets/PUBLISHING.md
- https://github.github.io/spec-kit/community/walkthroughs.html
- https://github.github.io/spec-kit/community/friends.html
- https://github.github.io/spec-kit/reference/integrations.html
- https://github.github.io/spec-kit/reference/overview.html
- https://github.github.io/spec-kit/reference/extensions.html
- https://github.github.io/spec-kit/reference/presets.html
- https://github.com/mnriem/spec-kit-pirate-speak-preset-demo
- https://www.python.org/downloads/
- https://git-scm.com/downloads
- https://pipx.pypa.io/
- https://github.com/github/spec-kit/releases
- https://docs.github.com/en/github-cli/github-cli
