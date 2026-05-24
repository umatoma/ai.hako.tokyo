# ai.hako.tokyo

Coding Agent（**Claude Code** / **GitHub Spec Kit** / **AWS AI-DLC** など）を使ったソフトウェア開発を、自分たちの仕事に**実際に適用する**ためのナレッジベース。

## このリポジトリで得られるもの

- 信頼できる一次情報（Anthropic 公式ブログ・ホワイトペーパー等）の**日本語訳**を、ベンダー別に検索可能な形で
- それを「明日から使える形」に落とした**プレイブック**（手順書）
- ベンダー横断のトピック整理（ライフサイクル・出力形式の選び方など）

ナレッジを溜めるだけのリポではなく、**訪問者が次のアクションを取れる**ことを目的にしている。

## ここから読む（やりたいこと別）

| あなたが今やりたいこと | まず読むファイル |
|---|---|
| 新しいリポに Claude Code を導入したい | [`playbooks/setup-claude-code-in-new-repo.md`](playbooks/setup-claude-code-in-new-repo.md) |
| `CLAUDE.md` の書き方を知りたい | [`playbooks/write-effective-claude-md.md`](playbooks/write-effective-claude-md.md) |
| Claude Code・Chat・Cowork のどれをいつ使うか | [`frameworks/anthropic-claude-code.md`](frameworks/anthropic-claude-code.md) |
| アイデア / MVP / Launch / Scale の段階別に AI をどう使うか | [`topics/ai-native-startup-lifecycle.md`](topics/ai-native-startup-lifecycle.md) |
| Claude Code から HTML で成果物を出すべき場面を知りたい | [`sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md`](sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md) |
| AI ネイティブなスタートアップの原典に当たりたい | [`sources/anthropic/docs/the-founders-playbook.md`](sources/anthropic/docs/the-founders-playbook.md) |
| 自分が見つけた記事をこのリポに取り込みたい | [`playbooks/ingest-source-from-web.md`](playbooks/ingest-source-from-web.md) |
| 現在何があるか一覧で見たい | [`INDEX.md`](INDEX.md) |

## ディレクトリの役割

- [`sources/`](sources/) — 一次情報の日本語訳（ベンダー別）。引用の出典として使う
- [`frameworks/`](frameworks/) — ベンダー別の整理ノート（1 ベンダー＝ 1 ノート基本）
- [`topics/`](topics/) — ベンダー横断のトピック整理
- [`playbooks/`](playbooks/) — 「明日から使う」実践レシピ
- [`_templates/`](_templates/) — 新規ノートのコピー元

## 貢献する（自分が学んだことを追加する）

このリポは「Claude Code に編集させる」ことを前提に設計されている。新しい記事・PDF を取り込むときは:

1. [`playbooks/ingest-source-from-web.md`](playbooks/ingest-source-from-web.md) の手順に沿って `sources/` に保存（必ず日本語訳）
2. 既存の `frameworks/` / `topics/` を更新するか、新規ノートを `_templates/` から作る
3. [`INDEX.md`](INDEX.md) に追記

詳細な規約（frontmatter・命名・PDF 取り扱い）は [`CLAUDE.md`](CLAUDE.md) に集約してある。

## ステータス

現状は Anthropic 系の取り込みが中心。GitHub Spec Kit と AWS AI-DLC は枠（`sources/github/spec-kit/`, `sources/aws/ai-dlc/`）だけ用意済みで、取り込み待ち。ベンダー横断の比較が育つほど [`topics/`](topics/) の価値が出る設計。
