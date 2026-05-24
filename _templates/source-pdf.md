---
title: 日本語訳のタイトル
title_original: Original Title
source_url: https://....pdf
captured_at: YYYY-MM-DD
published_at: YYYY-MM-DD
author: 著者名 / 発行元
original_language: en
tags: [tag1, tag2]
# このドキュメントを参照しているブログ等があれば：
# referenced_from:
#   - sources/<vendor>/blog/YYYY-MM-DD-...md
---

# 日本語訳のタイトル

<!-- page: 1 -->

[Figure: ページ 1 — 表紙の説明]

<!-- page: 2 -->

## 目次

- [第 1 章: ...](#第-1-章-) ............ p.3
- [第 2 章: ...](#第-2-章-) ............ p.N
- ...
- [参考資料 (Resources)](#参考資料-resources) ............ p.N

<!-- page: 3 -->

[Figure: ページ 3 — 章扉のイラストの説明]

# 第 1 章: 章タイトル

<!-- page: 4 -->

ここに本文の日本語訳。

## 節タイトル

段落、リスト、表、コードブロックを構造を保ったまま翻訳する。

| 列1 | 列2 |
|---|---|
| 値 | 値 |

> 重要な引用は原文を残し、直後に訳を併記する。

**ページ区切りのルール:**
- 各 PDF ページの始まりに `<!-- page: N -->` を入れる
- 図やイラストは `[Figure: ページ N — 内容の概要]` の形で位置と内容だけ残す（再現はオリジナル PDF を参照）
- 表は Markdown table に変換。崩れる場合はコードブロックで生のまま保持
