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

（未取り込み）

- 想定: `sources/github/spec-kit/` に GitHub Spec Kit 関連を追加予定

### AWS

（未取り込み）

- 想定: `sources/aws/ai-dlc/` に AWS AI Development Lifecycle 関連を追加予定

### Dify

（未取り込み）

- 想定: `sources/dify/` に Dify 関連ドキュメント・ブログを追加予定

### n8n

（未取り込み）

- 想定: `sources/n8n/` に n8n 関連ドキュメント・ブログを追加予定

---

## frameworks/ — ベンダー/ツール別の整理ノート

- [`anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) — Chat / Claude Cowork / Claude Code のサーフェス選択、HTML 出力の指針、CLAUDE.md 運用のお作法

---

## topics/ — 業務領域別のベンダー横断ノート

### software-development/

- [`ai-native-startup-lifecycle.md`](topics/software-development/ai-native-startup-lifecycle.md) — 4 段階モデル（Idea/MVP/Launch/Scale）の俯瞰。現状は Anthropic 単一視点

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

- 一次情報: 3 件（Anthropic ブログ 2 / PDF 1）
- 二次情報: 2 件（frameworks 1 / topics 1）
- プレイブック: 3 件（software-development 2 / knowledge-base 1）
- 業務領域: software-development が稼働、design/marketing/sales/hr/cross は枠のみ
- ベンダー/ツール: Anthropic が稼働、Google/GitHub/AWS/Dify/n8n は枠のみ
