# INDEX

このリポジトリに**現在何があるか**の一覧。CLAUDE.md が「どこに何を置くか（規約）」だとすれば、こちらは「実際に何が置いてあるか（現状）」。

新しいノートを追加・移動・削除したら、このファイルも更新する。

---

## sources/ — 一次情報（日本語訳）

### Anthropic

#### ブログ

- [`2026-05-14 The Founder's Playbook: AI ネイティブなスタートアップを作る`](sources/anthropic/blog/2026-05-14-the-founders-playbook.md) — 同名 PDF への入口記事
- [`2026-05-20 Claude Code を使う: HTML の不合理なまでの有効性`](sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md) — Markdown より HTML を成果物形式として好む理由・ユースケース

#### ドキュメント・ホワイトペーパー

- [`The Founder's Playbook (PDF 全 36 ページ Markdown 変換版)`](sources/anthropic/docs/the-founders-playbook.md) — Idea / MVP / Launch / Scale の 4 段階モデルと AI 活用

### GitHub

（未取り込み）

- 想定: `sources/github/spec-kit/` に GitHub Spec Kit 関連を追加予定

### AWS

（未取り込み）

- 想定: `sources/aws/ai-dlc/` に AWS AI Development Lifecycle 関連を追加予定

---

## frameworks/ — ベンダー別の整理ノート

- [`anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) — Chat / Claude Cowork / Claude Code のサーフェス選択、HTML 出力の指針、CLAUDE.md 運用のお作法

---

## topics/ — ベンダー横断の整理ノート

- [`ai-native-startup-lifecycle.md`](topics/ai-native-startup-lifecycle.md) — 4 段階モデル（Idea/MVP/Launch/Scale）の俯瞰。現状は Anthropic 単一視点

---

## playbooks/ — 実践用手順

- [`ingest-source-from-web.md`](playbooks/ingest-source-from-web.md) — ブログ・PDF を `sources/` に取り込む手順とチェックリスト

---

## _templates/ — テンプレート

- [`source-blog.md`](_templates/source-blog.md) — ブログ記事取り込み用
- [`source-pdf.md`](_templates/source-pdf.md) — PDF 取り込み用
- [`framework-or-topic.md`](_templates/framework-or-topic.md) — 二次情報ノート用

---

## 規約・運用

- [`CLAUDE.md`](CLAUDE.md) — ディレクトリ役割、frontmatter、PDF 取り扱い、言語ポリシー
- [`README.md`](README.md) — リポジトリ紹介（短く）

---

## 統計（参考）

- 一次情報: 3 件（Anthropic ブログ 2 / PDF 1）
- 二次情報: 2 件（frameworks 1 / topics 1）
- プレイブック: 1 件
- 未取り込みベンダー: GitHub Spec Kit / AWS AI-DLC
