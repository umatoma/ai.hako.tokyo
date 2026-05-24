# ai.hako.tokyo

AI を活用した**ソフトウェア開発**および**各種業務**（デザイン・マーケティング・営業・人事 など）を、自分たちの仕事に**実際に適用する**ためのナレッジベース。**Coding Agent**（Claude Code）、**開発手法・フレームワーク**（GitHub Spec Kit、AWS AI-DLC）、**個別ツール**（Dify、n8n、NotebookLM、Gemini、NanoBanana など）を横断的に扱う。

## このリポジトリで得られるもの

- 信頼できる一次情報（Anthropic 公式ブログ・ホワイトペーパー等）の**日本語訳**を、ベンダー別に検索可能な形で
- それを「明日から使える形」に落とした**プレイブック**（手順書）
- ベンダー横断のトピック整理（ライフサイクル・出力形式の選び方など）

ナレッジを溜めるだけのリポではなく、**訪問者が次のアクションを取れる**ことを目的にしている。

## ここから読む

訪問者の進行に沿った 4 フェーズに整理してある。エントリが増えるときは既存フェーズに追加するだけ。

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

### 3. 原典で確認する

二次情報に書かれた主張の根拠を辿りたいとき。

| 読みたい原典 | 読むファイル |
|---|---|
| The Founder's Playbook（PDF 全 36 ページの和訳） | [`sources/anthropic/docs/the-founders-playbook.md`](sources/anthropic/docs/the-founders-playbook.md) |
| Claude Code: HTML の不合理なまでの有効性（元ブログ） | [`sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md`](sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md) |

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

## ステータス

### 業務領域別の進捗

| 領域 | 状態 |
|---|---|
| software-development | 稼働中（Anthropic 系の取り込みベース） |
| design / marketing / sales / hr / cross | 枠のみ（README で意図を明示済み、コンテンツ待ち） |

### ベンダー/ツール別の進捗

| 対象 | 状態 |
|---|---|
| Anthropic（Claude / Claude Code） | 取り込み済み |
| Google（Gemini / NotebookLM / NanoBanana） | 枠のみ |
| GitHub Spec Kit | 枠のみ |
| AWS AI-DLC | 枠のみ |
| Dify | 枠のみ |
| n8n | 枠のみ |

ベンダー横断の比較・業務領域別のノートが育つほど [`topics/`](topics/) [`playbooks/`](playbooks/) の価値が出る設計。
