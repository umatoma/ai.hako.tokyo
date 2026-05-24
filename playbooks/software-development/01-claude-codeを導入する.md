---
title: 新規・既存リポジトリに Claude Code を導入するときの手順
updated: 2026-05-24
tags: [claude-code, setup, claude-md, scope, onboarding, playbook]
related_sources:
  - sources/anthropic/docs/the-founders-playbook.md
  - sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md
---

# 新規・既存リポジトリに Claude Code を導入するときの手順

Claude Code を「単発のコード生成器」ではなく「永続的な協働者」として使うための初期セットアップ。Founder's Playbook が MVP 章で繰り返し強調する以下の 4 点を「明日から動ける手順」に落としたもの:

1. アーキテクチャ・コンテキストを Claude（Chat）と先に作る
2. `CLAUDE.md` に保存する
3. **スコープ・ドキュメント**を別途用意する（やらないことを明文化）
4. 各セッションを揃える（開始＝読ませる／終了＝追記）

> 出典は [`frameworks/anthropic-claude-code.md`](../../frameworks/anthropic-claude-code.md) に集約。さらに深い根拠は [`sources/anthropic/docs/the-founders-playbook.md`](../../sources/anthropic/docs/the-founders-playbook.md) の MVP 章。

## 前提と適用範囲

- **適用**: チームの主開発エージェントとして Claude Code を使うリポジトリ。一度きりのスクリプト生成には不要。
- **規模感**: 新規 / 数千行の既存 / 数万行のレガシー、いずれにも適用可能（ステップ 2 の作り方だけ変わる）。
- **言語・FW 非依存**: 手順は中身（書く内容）ではなく形（どこに何を置くか）の話。

## ステップ 0: その前に - 検証はしたか

Founder's Playbook 全章で繰り返される警告：「Claude Code が作るのが楽すぎる」ため**検証を作ることで代替してしまう**。リポを切る前に、

- 解決しようとしている問題は具体的か（「契約レビューが遅い」ではなく「中堅企業の社内法務が 1 サイクル 3 日以上を赤入れメールに費やす」レベル）
- 実ユーザーがそれを抱えている証拠が一つでもあるか

を確認する。詳細は [`topics/software-development/ai-native-startup-lifecycle.md`](../../topics/software-development/ai-native-startup-lifecycle.md) Idea 段階を参照。

## ステップ 1: アーキテクチャ・スケッチを Claude（Chat）と作る

**Claude Code を起動する前に** Claude.ai か Claude Cowork で:

- システムを構成する主要なコンポーネント
- 採用するスタック（言語・FW・データストア・ホスティング）
- **意図的に避ける依存**（例:「認証はサードパーティ SaaS、自前で書かない」「リアルタイム同期は今は持たない」）
- **許容したトレードオフ**（例:「スループットより一貫性優先」「水平スケールは後回し」）

を 1 ページにまとめる。Founder's Playbook の表現を借りれば「Claude Code が本番コードを 1 行書く前に」決めておく事項。

出力形式は [HTML アーティファクト](../../sources/anthropic/blog/2026-05-20-unreasonable-effectiveness-of-html.md)推奨（コンポーネント図・データフロー・テーブルを 1 画面で見渡せる）。

## ステップ 2: `CLAUDE.md` を書く

リポのルートに `CLAUDE.md` を作り、Claude Code セッション開始時に自動で読まれる**永続メモリ**として使う。書き方の詳細は [`02-claude-mdを書く.md`](./02-claude-mdを書く.md) に分離。最低限載せるもの:

- このリポジトリの目的（1〜3 行）
- 主要コマンド（build / test / lint / dev サーバ）
- アーキテクチャの big picture（複数ファイル読まないと分からない部分のみ）
- ステップ 1 で決めた**避ける依存・許容したトレードオフ**
- コミット・PR 規約（あれば）

新規リポなら、Claude Code に `/init` させると初期版を作ってくれる。既存リポでもまず `/init` から始めてよい（その後手で削る）。

## ステップ 3: スコープ・ドキュメントを別途用意する

`CLAUDE.md` とは別に `SCOPE.md`（または `docs/scope.md`）を作り:

- 製品が**何をするか**
- **意図的にしないこと**（スコープアウト）
- **新機能を追加するに値する実ユーザーからのエビデンスの基準**（機能追加基準）

を書く。Founder's Playbook いわく「摩擦ゼロのスコープクリープ」がエージェント時代の特有の罠。「ユーザーの臨界量がこれなしには価値を得られないと言ったか？」を機能追加の判定に使う。

`CLAUDE.md` に「新機能の提案前に `SCOPE.md` を読み、スコープアウトと矛盾しないか確認する」と書いておく。

## ステップ 4: セッション開始・終了のルーチンを決める

Founder's Playbook の「5 分のドキュメント化はアーキテクチャ・ドリフトに対する安価な保険」を運用に落とす:

**セッション開始時:**

- `CLAUDE.md` と `SCOPE.md` を Claude Code に読ませる（自動で `CLAUDE.md` は読まれるが、`SCOPE.md` は明示的に指す）
- そのセッションのゴールを 1 文で宣言する

**セッション終了時 (重要):**

- そのセッションで**決定したこと**・**導入した仮定**を `CLAUDE.md` に追記する
- 仮実装・TODO は `CLAUDE.md` ではなくコード中の `TODO` か Issue に書く（`CLAUDE.md` は揮発性の低い情報用）

このルーチンを `CLAUDE.md` 末尾に「セッション運用」セクションとして書いておくと、Claude Code が自分で守るようになる。

## ステップ 5: セキュリティ・チェックポイントを決めておく

Founder's Playbook の警告:「エージェント型コーディングは**動くコードを生むが本来的に安全なコードは生まない**」。ユーザーが触れる前に通すレビュー基準を 1 つでも決めておく。最小例:

- 認証・認可を触る PR は人間レビュー必須
- 外部入力のバリデーション・SQL/コマンドインジェクション系は自動 lint + 人間チェック
- シークレットを含むファイルパターン（`.env`, `*.pem`, `credentials.json`）をコミットフックで弾く

これも `CLAUDE.md` の「やってはいけないこと」に書き、Claude Code に守らせる。

## ステップ 6: 「`make an HTML file`」を使えるようにする

Claude Code に何かしらの中間成果物（仕様・レビュー結果・設計案）を出させるとき、デフォルトで HTML アーティファクトを使う:

- 仕様・計画 → 複数案を 1 画面で比較
- コードレビュー → 重大度色分け
- 進捗レポート → ソース横断（git / Slack / コード）の要約

詳細は [`frameworks/anthropic-claude-code.md` の「HTML vs Markdown」](../../frameworks/anthropic-claude-code.md#claude-code-出力の選び方html-vs-markdown)。

## チェックリスト

- [ ] アーキテクチャ・スケッチを Chat 側で作った（避ける依存・許容したトレードオフを明示）
- [ ] `CLAUDE.md` をルートに置いた（コマンド・big picture・規約）
- [ ] `SCOPE.md` を作って機能追加基準を書いた
- [ ] セッション開始・終了ルーチンを `CLAUDE.md` 末尾に書いた
- [ ] セキュリティ・チェックポイントを 1 つ以上決めた
- [ ] HTML アーティファクト出力を試した（最初の 1 回でいい）

## 関連

- [`02-claude-mdを書く.md`](./02-claude-mdを書く.md) — `CLAUDE.md` の中身の書き方
- [`../knowledge-base/01-外部情報を取り込む.md`](../knowledge-base/01-外部情報を取り込む.md) — 学んだ知見をこのリポに取り込む手順
- [`frameworks/anthropic-claude-code.md`](../../frameworks/anthropic-claude-code.md) — サーフェス選択・HTML 出力指針
- [`topics/software-development/ai-native-startup-lifecycle.md`](../../topics/software-development/ai-native-startup-lifecycle.md) — どの段階で何を優先するか
