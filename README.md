# ai.hako.tokyo

AI を活用した**ソフトウェア開発**および**各種業務**（デザイン・マーケティング・営業・人事 など）を、自分たちの仕事に**実際に適用する**ためのナレッジベース。**Coding Agent**（Claude Code）、**開発手法・フレームワーク**（GitHub Spec Kit、AWS AI-DLC、GSD など）、**個別ツール**（Dify、n8n、NotebookLM、Gemini、NanoBanana など）を横断的に扱う。

## このリポジトリで得られるもの

- 信頼できる一次情報（Anthropic 公式ブログ・ホワイトペーパー等）の**日本語訳**を、ベンダー別に検索可能な形で
- それを「明日から使える形」に落とした**プレイブック**（手順書）
- ベンダー横断のトピック整理（ライフサイクル・出力形式の選び方など）

ナレッジを溜めるだけのリポではなく、**訪問者が次のアクションを取れる**ことを目的にしている。

## ここから読む

訪問者の進行に沿った 4 フェーズに整理してある。エントリが増えるときは既存フェーズに追加するだけ。以下は**実際にコンテンツがあるもの**のみ。業務領域・ベンダー別の入口（枠だけのものも含む）は下の「[業務領域別の入口](#業務領域別の入口)」「[ベンダー/ツール別の入口](#ベンダーツール別の入口)」を参照。

### 1. まず始める（実践プレイブック）

「明日から手を動かす」ためのレシピ。

| やりたいこと | 読むファイル |
|---|---|
| 新規・既存リポに Claude Code を導入する | [`playbooks/software-development/01-claude-codeを導入する.md`](playbooks/software-development/01-claude-codeを導入する.md) |
| `CLAUDE.md` を書く・育てる | [`playbooks/software-development/02-claude-mdを書く.md`](playbooks/software-development/02-claude-mdを書く.md) |

### 2. 判断する（使い分け・原則）

複数の選択肢から「どれを選ぶか」の指針。

| 判断したいこと | 読むファイル |
|---|---|
| Claude Code / Chat / Cowork のどれをいつ使うか | [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) |
| Idea / MVP / Launch / Scale の段階別に AI で何を優先するか | [`topics/software-development/ai-native-startup-lifecycle.md`](topics/software-development/ai-native-startup-lifecycle.md) |
| Claude Code の出力を HTML / Markdown で使い分ける | [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md#claude-code-出力の選び方html-vs-markdown) |
| GitHub Spec Kit とは何か / どこに効くか | [`frameworks/github-spec-kit.md`](frameworks/github-spec-kit.md) |
| AWS AI-DLC とは何か / Mob 様式と Bolts | [`frameworks/aws-ai-dlc.md`](frameworks/aws-ai-dlc.md) |
| GSD (Get Shit Done Redux) の 6 コマンドループとは | [`frameworks/open-gsd-get-shit-done-redux.md`](frameworks/open-gsd-get-shit-done-redux.md) |
| **Spec Kit / AI-DLC / GSD を使い分ける** | [`topics/software-development/ai-sdlc-methodologies-compared.md`](topics/software-development/ai-sdlc-methodologies-compared.md) |

### 3. 原典で確認する

二次情報に書かれた主張の根拠を辿りたいとき。代表的なものだけ。全件は [`INDEX.md`](INDEX.md) を参照。

| 読みたい原典 | 読むファイル |
|---|---|
| The Founder's Playbook（PDF 全 36 ページの和訳） | [`sources/anthropic/docs/the-founders-playbook.md`](sources/anthropic/docs/the-founders-playbook.md) |
| Claude Code: HTML の不合理なまでの有効性（元ブログ） | [`sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md`](sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md) |
| GitHub Spec Kit リポジトリ README | [`sources/github/spec-kit/readme.md`](sources/github/spec-kit/readme.md) |
| Spec-Driven Development メソドロジー解説 | [`sources/github/spec-kit/spec-driven.md`](sources/github/spec-kit/spec-driven.md) |
| AWS AI-DLC 発表記事（"central collaborator"） | [`sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md`](sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md) |
| AI-DLC ワークフローリポジトリ README | [`sources/aws/ai-dlc/aidlc-workflows-readme.md`](sources/aws/ai-dlc/aidlc-workflows-readme.md) |
| GSD (Get Shit Done Redux) リポジトリ README | [`sources/open-gsd/get-shit-done-redux/readme.md`](sources/open-gsd/get-shit-done-redux/readme.md) |

### 4. このリポを育てる（貢献）

学んだことを追加する側に回るとき。

| やりたいこと | 読むファイル |
|---|---|
| 自分が見つけた記事・PDF をこのリポに取り込む | [`playbooks/knowledge-base/01-外部情報を取り込む.md`](playbooks/knowledge-base/01-外部情報を取り込む.md) |
| 現在何があるか一覧で見る | [`INDEX.md`](INDEX.md) |

## ディレクトリの役割

- [`sources/`](sources/) — 一次情報の日本語訳（ベンダー/ツール別）。引用の出典として使う
- [`frameworks/`](frameworks/) — ベンダー/ツール別の整理ノート（1 ベンダー＝ 1 ノート基本）
- [`topics/`](topics/) — **業務領域別**のベンダー横断トピック（`software-development/` `design/` `marketing/` `sales/` `hr/` `cross/`）
- [`playbooks/`](playbooks/) — **業務領域別**の実践レシピ。リポ自体の運用は `playbooks/knowledge-base/`
- [`_templates/`](_templates/) — 新規ノートのコピー元

## 貢献する（自分が学んだことを追加する）

このリポは「Claude Code に編集させる」ことを前提に設計されている。新しい記事・PDF を取り込むときは:

1. [`playbooks/knowledge-base/01-外部情報を取り込む.md`](playbooks/knowledge-base/01-外部情報を取り込む.md) の手順に沿って `sources/` に保存（必ず日本語訳）
2. 既存の `frameworks/` / `topics/` を更新するか、新規ノートを `_templates/` から作る
3. [`INDEX.md`](INDEX.md) に追記

詳細な規約（frontmatter・命名・PDF 取り扱い）は [`CLAUDE.md`](CLAUDE.md) に集約してある。

## 業務領域別の入口

各業務領域での AI 活用に関する整理ノート (`topics/`) と実践レシピ (`playbooks/`) の入口。枠だけのディレクトリも README で扱う範囲を明示してある。

| 領域 | topics（横断トピック） | playbooks（実践手順） | 状態 |
|---|---|---|---|
| ソフトウェア開発 | [`topics/software-development/`](topics/software-development/) | [`playbooks/software-development/`](playbooks/software-development/) | 稼働中（Anthropic / Spec Kit / AI-DLC / GSD） |
| デザイン | [`topics/design/`](topics/design/) | [`playbooks/design/`](playbooks/design/) | 枠のみ |
| マーケティング | [`topics/marketing/`](topics/marketing/) | [`playbooks/marketing/`](playbooks/marketing/) | 枠のみ |
| 営業 | [`topics/sales/`](topics/sales/) | [`playbooks/sales/`](playbooks/sales/) | 枠のみ |
| 人事 | [`topics/hr/`](topics/hr/) | [`playbooks/hr/`](playbooks/hr/) | 枠のみ |
| 業務横断 | [`topics/cross/`](topics/cross/) | — | 枠のみ |
| このリポ運用 | — | [`playbooks/knowledge-base/`](playbooks/knowledge-base/) | 稼働中 |

## ベンダー/ツール別の入口

一次情報 (`sources/`) と整理ノート (`frameworks/`) の入口。

| 対象 | sources（一次情報） | frameworks（整理ノート） | 状態 |
|---|---|---|---|
| Anthropic（Claude / Claude Code） | [`sources/anthropic/`](sources/anthropic/) | [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) | 取り込み済み |
| GitHub Spec Kit | [`sources/github/spec-kit/`](sources/github/spec-kit/) | [`frameworks/github-spec-kit.md`](frameworks/github-spec-kit.md) | 取り込み済み |
| AWS AI-DLC | [`sources/aws/ai-dlc/`](sources/aws/ai-dlc/) | [`frameworks/aws-ai-dlc.md`](frameworks/aws-ai-dlc.md) | 取り込み済み |
| GSD (open-gsd / Get Shit Done Redux) | [`sources/open-gsd/`](sources/open-gsd/) | [`frameworks/open-gsd-get-shit-done-redux.md`](frameworks/open-gsd-get-shit-done-redux.md) | 取り込み済み |
| Google（Gemini / NotebookLM / NanoBanana） | [`sources/google/`](sources/google/) | — | 枠のみ |
| Dify | [`sources/dify/`](sources/dify/) | — | 枠のみ |
| n8n | [`sources/n8n/`](sources/n8n/) | — | 枠のみ |

ベンダー横断の比較・業務領域別のノートが育つほど [`topics/`](topics/) [`playbooks/`](playbooks/) の価値が出る設計。
