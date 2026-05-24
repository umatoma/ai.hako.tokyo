# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## このリポジトリの目的

Coding Agent（Claude Code、GitHub Spec Kit、AWS AI-DLC など）を活用したソフトウェア開発に関する知見を蓄積・整理するナレッジベース。インターネット上の重要な情報源をローカルに取り込み、整理・要約したノートと並べて管理する。

## 言語

- ユーザーとのやり取りは常に日本語で行う。
- リポジトリ内のドキュメント・ノートも原則として日本語で記述する。
- ただし以下はそのまま原語を維持する：
  - 固有名詞・製品名（Claude Code, Anthropic, GitHub Spec Kit, AWS AI-DLC など）
  - コード片・コマンド・パス・URL
  - 引用したい原文の一節（`> "..."` の形で原文を残し、直後に日本語訳を併記）
- `sources/` に取り込む一次情報も**日本語に翻訳して保存する**（読みやすさ優先）。原文 URL を frontmatter に必ず残し、原典に立ち返れるようにする。
- 翻訳は構造（見出し・段落・リスト・コード）を保ち、内容の追加・削除はしない（要約ではなく翻訳）。判断に迷う訳語は原語を括弧書きで併記する（例：「文脈窓 (context window)」）。

## ディレクトリの役割

| ディレクトリ | 役割 | 中身の性質 |
|---|---|---|
| `sources/` | 一次情報の日本語訳をベンダー別に保存。引用の出典として参照 | 取り込み元に忠実（翻訳） |
| `frameworks/` | ベンダーごとの開発手法・フレームワークの整理ノート（1ベンダー＝1ノートを基本） | 二次情報・要約 |
| `topics/` | ベンダー横断のトピック別ノート（プロンプティング、エージェント設計、評価、コンテキスト管理など） | 二次情報・比較 |
| `playbooks/` | 自分たちの作業手順・レシピ。明日から使える形に落とし込んだもの | 実践用 |

どこに置くべきか迷ったときの判断ルール：

- **原文/引用したいページ** → `sources/<vendor>/<category>/`
- **ある製品・フレームワーク単体の解説** → `frameworks/`
- **複数製品を横断する概念の整理** → `topics/`
- **「こうやって作業する」という手順** → `playbooks/`

## ファイル命名

- `sources/` 配下のブログ・記事：`YYYY-MM-DD-slug.md`（公開日ベース、不明なら取得日）
- `sources/` 配下のドキュメント：`slug.md`（バージョンが必要なら `slug-v2.md`）
- それ以外：`kebab-case.md`

## frontmatter

### `sources/` 配下（一次情報の取り込み）

```yaml
---
title: 日本語訳のタイトル
title_original: Original Title
source_url: https://...
captured_at: 2026-05-24   # ローカルに取り込んだ日
published_at: 2026-05-01  # 元記事の公開日（分かれば）
author: 著者名
original_language: en
tags: [agents, prompting]
related_docs:              # 同じ記事から派生した PDF などの Markdown 変換版（あれば）
  - sources/anthropic/docs/foo.md
---
```

本文は構造を保った日本語訳。要約する場合は冒頭に「要約」と明記し、`title` にも「（要約）」を付ける。

### `frameworks/` / `topics/` / `playbooks/`（二次情報）

```yaml
---
title: ノートのタイトル
updated: 2026-05-24
tags: [...]
related_sources:
  - sources/anthropic/blog/2026-05-01-...md
  - sources/github/spec-kit/...md
---
```

参照した一次情報は `related_sources` に必ずリンクする（リポジトリ相対パス）。出典のないノートは作らない。

## 情報を取り込むときの作業フロー

1. `WebFetch` で対象ページを取得する。
2. 内容を日本語に翻訳し、構造を保ったまま `sources/<vendor>/<category>/` に frontmatter 付きで保存する。
3. 元ページから PDF（ホワイトペーパー・プレイブック等）がリンクされていれば、その PDF も取り込む（次節「PDF の取り扱い」参照）。元ページ側 frontmatter の `related_docs` に PDF の Markdown 変換版へのリンクを追加する。
4. 既存の `frameworks/` または `topics/` ノートを更新、または新規作成し、`related_sources` でリンクする。
5. 古くなった情報を見つけたら frontmatter の `updated` / `captured_at` を更新するか、新バージョンとして別ファイルを追加する。

## PDF の取り扱い

- PDF を一次情報として取り込むときは、必ず Markdown に変換して `sources/<vendor>/docs/` に保存する。
- 変換後の Markdown を一次情報として扱い、PDF バイナリは原則リポジトリに保存しない（オリジナルは frontmatter の `source_url` から取得できる）。
- `WebFetch` に PDF の URL を渡すと、ツールがローカルにバイナリ保存し、そのパスをメッセージで返す。それを `Read` の `pages` パラメータで章単位に読み出す（最大 20 ページ/回）。これが標準フロー。
- 変換時のルール：
  - 章構造・見出し・リスト・コードは保つ。
  - ページ区切りは `<!-- page: N -->` のコメントで明示する。
  - 図やイラストは `[Figure: ページ N — 概要]` のように位置と内容の概要だけ残す（再現はオリジナル PDF を参照）。
  - 表は Markdown table に変換する（崩れる場合はコードブロックで生のまま保持）。
- Claude のブログ記事を取り込む際にホワイトペーパー・PDF へのリンクが本文にある場合は、ブログ本体だけでなくその PDF も取り込む。

## 新しいベンダー/カテゴリを追加するとき

`sources/<vendor>/` を新設したら、その配下に `README.md` を 1 つ置いて「何を集めているディレクトリか」を 1〜3 行で説明する。空ディレクトリは作らない（git で追跡されない）。

## やらないこと

- 推測でノートを書かない。出典が辿れない記述は載せない。
- 同じ内容を `frameworks/` と `topics/` の両方に重複させない。片方に書いてもう片方からリンクする。
- 大量の生コピーを `frameworks/` / `topics/` 配下に置かない（それは `sources/` の役割）。
- 翻訳と称して要約にすり替えない。要約する場合は冒頭で明示する。
- PDF をそのまま `.pdf` として保存しない。必ず `.md` に変換する。
