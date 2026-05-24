# sources/

外部から取得した一次情報をベンダー別に保存する。引用の出典として参照する場所。

## 現在のベンダー

- `anthropic/blog/` — https://www.anthropic.com/news, https://claude.com/blog などの記事
- `anthropic/docs/` — Claude / Claude Code の公式ドキュメント
- `github/spec-kit/` — GitHub Spec Kit（仕様駆動開発ツールキット）に関するドキュメント・ブログ
- `aws/ai-dlc/` — AWS AI Development Lifecycle に関する資料
- `google/` — Gemini / NotebookLM / NanoBanana など Google の AI プロダクト
- `dify/` — Dify（LLM アプリ開発プラットフォーム）
- `n8n/` — n8n（オープンソースのワークフロー自動化ツール）
- `others/` — 上記に当てはまらないもの。たまったらベンダー別に切り出す

## 取り込みルール

frontmatter と命名規則は [../CLAUDE.md](../CLAUDE.md#frontmatter) を参照。

新しいベンダーを追加するときは `sources/<vendor>/README.md` を 1〜3 行で書いてから記事を入れる。
