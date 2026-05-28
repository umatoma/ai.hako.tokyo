---
title: "GET SHIT DONE Redux README (open-gsd 公式リポジトリ)"
title_original: "GET SHIT DONE — A light-weight meta-prompting, context engineering, and spec-driven development system"
source_url: https://github.com/open-gsd/get-shit-done-redux
captured_at: 2026-05-28
published_at: 2026-05-24
author: open-gsd team
original_language: en
tags: [gsd, get-shit-done-redux, open-gsd, claude-code, opencode, gemini-cli, codex, copilot, cursor, windsurf, context-engineering, multi-agent, spec-driven-development]
---

> 取り込みメモ: open-gsd team の公式リポジトリ README（`next` ブランチ / v1.1.0 リリース時点）の日本語訳。WebFetch で取得した Markdown を翻訳。インストールコマンド・コマンド名・パスは原文のまま残す。冒頭の「Project Continuity Notice」も忠実に訳した（プロジェクトの正当性・経緯を示す重要部分）。

# GET SHIT DONE Redux

> **プロジェクト継続性のお知らせ**
>
> GSD は **open-gsd** チーム（リポジトリ: **`open-gsd/get-shit-done-redux`**）によって保守されている。
>
> 使用するべきパッケージ名は次のもののみ:
>
> - npm (main): `@opengsd/get-shit-done-redux`
> - npm (sdk): `@opengsd/gsd-sdk`
>
> 旧来のアップストリームは open-gsd の統制下にない。公開された移行アナウンスとリポジトリ所有の実態に基づき、レガシーパッケージを削除して `@opengsd/*` へ移行することを強く推奨する。
>
> セキュリティステータス:
>
> - メンテナーは内部セキュリティ監査を完了
> - メンテナーは独立レビューが通ったと報告
> - 追跡対象のソースで、これらのパスにおいて既知のアクティブな脆弱性は発見されなかった
>
> 参照:
>
> - 継続性アナウンス: [#109](https://github.com/open-gsd/get-shit-done-redux/discussions/109)
> - 監査透明性レポート: [#119](https://github.com/open-gsd/get-shit-done-redux/discussions/119)

---

## GET SHIT DONE

**English** · [Português](https://github.com/open-gsd/get-shit-done-redux/blob/next/README.pt-BR.md) · [简体中文](https://github.com/open-gsd/get-shit-done-redux/blob/next/README.zh-CN.md) · [日本語](https://github.com/open-gsd/get-shit-done-redux/blob/next/README.ja-JP.md) · [한국어](https://github.com/open-gsd/get-shit-done-redux/blob/next/README.ko-KR.md)

**Claude Code、OpenCode、Gemini CLI、Kilo、Codex、Copilot、Cursor、Windsurf などのための、軽量なメタプロンプティング・コンテキストエンジニアリング・仕様駆動開発システム。**

**コンテキスト腐敗 (context rot) を解決する** ― AI が文脈窓を埋めるにつれて起こる品質低下のこと。

**Mac、Windows、Linux で動く。**

### インストール

```
npx @opengsd/get-shit-done-redux@latest
```

### ユーザーの声

> 「何が欲しいかを明確にわかっているなら、これがそれを作ってくれる。ごまかしなしに。」

> 「SpecKit、OpenSpec、Taskmaster をやってきた ― これが私には一番良い結果を出した。」

> 「Claude Code への追加機能として群を抜いて強力。過剰設計が何もない。文字通り、ただ shit を done する。」

**Amazon、Google、Shopify、Webflow のエンジニアたちが信頼している。**

---

## 重要: GSD に戻ってきたとき

`/gsd-map-codebase` でコードベースを再インデックスし、その後 `/gsd-new-project` で GSD の計画コンテキストを再構築する。コードは大丈夫 ― GSD はコンテキストを再構築する必要があるだけ。新機能は [CHANGELOG](https://github.com/open-gsd/get-shit-done-redux/blob/next/CHANGELOG.md) を参照。

---

## なぜ GSD を作り続けるのか

GSD は、ソロビルダーと小規模チームが AI とともに信頼できる出荷をするために存在する: 明確な仕様、統制された文脈、リリース前の検証。

2026 年 5 月、メンテナーは継続性アナウンスを公開し、旧アップストリーム周辺の信頼と所有権の懸念（そのエコシステムに公に関連付けられた meme-coin の rug-pull 事件を含む）を受けて、アクティブな開発を `open-gsd/get-shit-done-redux` に移行した。

旧クリエイターとレガシー系譜はこのプログラムにはもう含まれない。このリポジトリが open-gsd ガバナンス下の保守された継続版である。

現チームはリリース運用・トリアージ・セキュリティ強化を公開で続けている。監査ステータスとフォローアップのセキュリティ作業は Discussion #119 とリンクされた Issue で文書化されている。

---

## どう動くか

ループは 6 コマンド。各コマンドは正確に 1 つのことだけをする。

### 1. 初期化

```
/gsd-new-project
```

質問 → リサーチ → 要件 → ロードマップ。承認すれば、構築準備完了。

> **既にコードがある？** まず `/gsd-map-codebase` を実行する。これがスタック・アーキテクチャ・慣習を分析し、`/gsd-new-project` が正しい質問をできるようにする。

### 2. ディスカス（議論）

```
/gsd-discuss-phase 1
```

ロードマップは 1 フェーズに 1 文しかない。それでは「**あなた**が思い描いた通り」に作るには足りない。ディスカスは計画を始める前にあなたの判断を捕まえる: レイアウト、API の形、エラーハンドリング、データ構造 ― 特定フェーズに存在する任意のグレー領域について。

出力は直接リサーチと計画に供給される。スキップすれば「妥当なデフォルト」になる。使えば「あなたのビジョン」になる。

### 3. 計画

```
/gsd-plan-phase 1
```

リサーチ → 計画 → 検証 を、計画がパスするまでループ。各計画は、新しい文脈窓 (fresh context window) で実行できる十分小ささに保たれる。

### 4. 実行

```
/gsd-execute-phase 1
```

計画は並列の「**波 (waves)**」で実行される。各エグゼキューターは新鮮な 200k トークンの文脈を得る。各タスクは独自のアトミックコミットを得る。立ち去って戻れば、クリーンな git 履歴と完成した作業が待っている。

メイン文脈窓は 30–40% に保たれる。作業はサブエージェント内で行われる。

### 5. 検証

```
/gsd-verify-work 1
```

構築されたものを順に確認する。壊れているものには診断された修正計画 ― 即座に再実行できる状態 ― が付く。手動デバッグはしない。実行を再度走らせるだけ。

### 6. 反復 → 出荷

```
/gsd-ship 1
/gsd-complete-milestone
/gsd-new-milestone
```

discuss → plan → execute → verify → ship をマイルストーンが完了するまでループ。完了したらアーカイブ・タグ付けし、次を新鮮な状態で開始。

---

## はじめる

```
npx @opengsd/get-shit-done-redux@latest
```

インストーラーがランタイム（Claude Code、OpenCode、Gemini CLI、Kilo、Codex、Copilot、Cursor、Windsurf など）と、グローバル/ローカルインストールを尋ねる。

```
claude --dangerously-skip-permissions
```

GSD は摩擦のない自動化のために作られている。Skip-permissions は意図された実行方法。

必要なスキルだけインストールするには次のフラグを使う:

- `--profile=core` — 6 つのコアループスキル
- `--profile=standard` — コア + フェーズ管理
- 既定（デフォルト） — フルインストール

プロファイルは合成可能: `--profile=core,audit`。`--minimal` は `--profile=core` のエイリアス。完全なウォークスルー、15 ランタイムすべての非対話インストールフラグ、権限設定は **[docs/USER-GUIDE.md](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/USER-GUIDE.md)** を参照。プロファイルモデルとランタイム表面制御は [ADR-0011](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/adr/0011-skill-surface-budget-module.md) を参照。

現リリースのハイライトは [docs/RELEASE-v1.42.1.md](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/RELEASE-v1.42.1.md) にある: パッケージ正当性チェック、安全性を高めたインストーラー移行、ランタイム表面制御、カスタム ship PR セクション、レビュアーデフォルト、fallow 構造レビュー、クォータ認識実行リカバリ。

### クロスランタイム互換性: インストーラー必須

リポジトリの `agents/` と `commands/` ディレクトリは Claude Code フォーマットのソースファイル。インストーラー (`npx @opengsd/get-shit-done-redux@latest`) はターゲットランタイムごとにこれを変換する ― Claude Code が使うが他ランタイムが拒否する frontmatter フィールドを剥がしたり変換したりする。例えば OpenCode は `color` を固定セットの 16 進値または意味値として要求し、`tools:` frontmatter フィールドを受け付けない。インストーラー関数 `convertClaudeToOpencodeFrontmatter`（`bin/install.js`）が自動的にこれを処理する。

**ファイルを手動コピーする**こと ― `agents/` や `commands/` から非 Claude Code ランタイムの設定ディレクトリ（例: `~/.config/opencode/agents`）に直接 ― は変換ステップを飛ばし、そのランタイムでスキーマ検証エラーを生む。

Node.js や npm がないシステム（Windows + OpenCode が最も一般的なケース）の場合、**[docs/USER-GUIDE.md — Manual install / no-Node.js setup](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/USER-GUIDE.md#manual-install--no-nodejs-setup)** でランタイム別変換サマリと代替インストール経路を参照。

---

## コマンド

メインループ:

| コマンド | 何をするか |
|---|---|
| `/gsd-new-project` | 質問 → リサーチ → 要件 → ロードマップ |
| `/gsd-discuss-phase [N]` | 計画前に実装判断を捕まえる |
| `/gsd-plan-phase [N]` | リサーチ＋計画＋検証 |
| `/gsd-execute-phase <N>` | 計画を並列波で実行 |
| `/gsd-verify-work [N]` | 手動受け入れテスト |
| `/gsd-ship [N]` | 検証済みフェーズ作業から PR を作成 |
| `/gsd-progress --next` | 次のステップを自動検出して実行 |
| `/gsd-complete-milestone` | マイルストーンをアーカイブしてリリースタグ |
| `/gsd-new-milestone` | 次バージョンを開始 |
| `/gsd:surface` | 再インストールせずに実行時にスキルクラスタを有効/無効化 |

アドホックタスク、自律モード、コードベース分析、フォレンジック、完全なコマンドサーフェスは **[docs/COMMANDS.md](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/COMMANDS.md)** を参照。

---

## なぜ効くか

ほとんどの AI コーディングセットアップが間違える 3 つのこと:

**1. コンテキスト肥大化 (Context bloat)。** セッションが伸びると品質は劣化する。GSD は新鮮なサブエージェント文脈で重作業をすることで、メイン文脈をクリーンに保つ。リサーチャー・プランナー・エグゼキューターはそれぞれ、必要なものだけを持って新鮮にスタートする。

**2. 共有メモリの欠如 (No shared memory)。** GSD はセッション境界を越えて生き残る構造化された成果物を保守する: `PROJECT.md`（ビジョン）、`REQUIREMENTS.md`（スコープ）、`ROADMAP.md`（向かう先）、`STATE.md`（現位置と判断）、`CONTEXT.md`（フェーズごとの実装判断）。すべての新しいセッションがこれらをロードし、物事がどこに立っているかを正確に知る。

**3. 検証の欠如 (No verification)。** 「走る」コードは「動く」コードではない。GSD の検証ステップは構築されたものを順にウォークスルーし、専用デバッグエージェントで失敗を診断し、フェーズ完了宣言の前に修正計画を生成する。

マルチエージェントオーケストレーションとコンテキストエンジニアリングの詳細は **[docs/ARCHITECTURE.md](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/ARCHITECTURE.md)** を参照。

---

## 設定

設定は `.planning/config.json` に置かれる。`/gsd-new-project` で設定するか、`/gsd-settings` で更新する。

主要なつまみ:

| 設定 | 制御するもの |
|---|---|
| `mode` | `interactive`（各ステップを確認）または `yolo`（自動承認） |
| Model profiles | `quality` / `balanced` / `budget` — 各エージェントが使うモデルを制御 |
| `workflow.research` / `plan_check` / `verifier` | トークンと時間を加える品質エージェントの切替 |
| `parallelization.enabled` | 独立した計画を同時実行 |

オプションの構造レビュー: `code_quality.fallow.enabled` を `true` にすると `/gsd-code-review` に fallow プレパスを追加する。GSD は `.planning/phases/<phase>/FALLOW.json` を書き、`REVIEW.md` に `Structural Findings (fallow)` セクションを浮上させる。インストールは `npm install -D fallow@^2.70.0`（または `cargo install fallow` でシステム全体にインストール。Rust バイナリの JSON スキーマは文書化された v2.70+ 契約と一致する必要がある ― 古いバージョンは無音で 0 件出力を出すことがある）。

パッケージ正当性チェックはリサーチ・計画・実行パスに組み込まれている: 推奨された依存関係は監査され、未検証のパッケージは人間のチェックポイントを要求し、失敗したインストールは類似名の代替を試みるのではなく停止する。

完全な設定リファレンス ― すべての設定、git ブランチ戦略、ランタイム別モデル上書き、ワークストリーム設定継承、エージェントスキル注入 ― は **[docs/CONFIGURATION.md](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/CONFIGURATION.md)** を参照。

---

## ドキュメント

| Doc | 内容 |
|---|---|
| [User Guide](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/USER-GUIDE.md) | エンドツーエンドウォークスルー、インストールオプション、全ランタイムフラグ、設定リファレンス |
| [Commands](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/COMMANDS.md) | フラグと例を持つすべてのコマンド |
| [Configuration](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/CONFIGURATION.md) | フル設定スキーマ、モデルプロファイル、git ブランチング |
| [Architecture](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/ARCHITECTURE.md) | マルチエージェントオーケストレーションの仕組み |
| [CLI Tools](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/CLI-TOOLS.md) | `gsd-sdk query` とプログラマティック SDK ディスパッチシーム |
| [Features](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/FEATURES.md) | 完全な機能インデックス |
| [Changelog](https://github.com/open-gsd/get-shit-done-redux/blob/next/CHANGELOG.md) | 各リリースの変更 |

---

## トラブルシュート

**コマンドが表示されない？** インストール後にランタイムを再起動する。GSD は `~/.claude/skills/gsd-*/`（Claude Code）、`~/.codex/skills/gsd-*/`（Codex）、または同等のランタイム用ディレクトリにインストールされる。

**Codex ユーザー ― サポートされる最低 CLI バージョンは `0.130.0`。** Codex CLI 0.130.0 ([リリースノート](https://github.com/openai/codex/releases/tag/rust-v0.130.0)) は [openai/codex#21485](https://github.com/openai/codex/pull/21485) で追加スキルルート探索を削除した。そのバージョン以降、Codex は標準ルート（`~/.codex/skills/<name>/SKILL.md` を含む）からスキルを探す。GSD はそこに直接インストールする。古い Codex CLI バージョンはまだ追加ルートを探すかもしれず、それは重複した `gsd-*` エントリ（一方は追加ルート探索から、もう一方は `~/.codex/skills/` から）を浮上させうる。インストール後に Codex を再起動し、アップグレードするか重複表示を受け入れる。

**何かが壊れている？** インストーラーを再実行する ― 冪等:

```
npx @opengsd/get-shit-done-redux@latest
```

**コンテナや Docker？** ティルダ展開の問題を避けるため、インストール前に `CLAUDE_CONFIG_DIR` を設定する:

```
CLAUDE_CONFIG_DIR=/home/youruser/.claude npx @opengsd/get-shit-done-redux --global
```

完全なトラブルシュートとアンインストール手順は **[docs/USER-GUIDE.md](https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/USER-GUIDE.md#troubleshooting)** を参照。

---

## コミュニティ

| プロジェクト | プラットフォーム |
|---|---|
| [gsd-opencode](https://github.com/rokicool/gsd-opencode) | オリジナル OpenCode 移植 |
| [Discord](https://discord.gg/mYgfVNfA2r) | コミュニティサポート |

---

## ライセンス

MIT ライセンス。詳細は [LICENSE](https://github.com/open-gsd/get-shit-done-redux/blob/next/LICENSE) を参照。

---

## リポジトリメタデータ（取得時点 2026-05-28）

- **リポジトリ:** open-gsd/get-shit-done-redux
- **ブランチ:** next
- **最新リリース:** v1.1.0（2026-05-24）
- **スター:** 1.5k
- **フォーク:** 84
- **主要言語:** JavaScript (98.2%)
- **ライセンス:** MIT

## 関連ドキュメント URL（原文末尾より）

- https://github.com/open-gsd/get-shit-done-redux/discussions/109 — 継続性アナウンス
- https://github.com/open-gsd/get-shit-done-redux/discussions/119 — 監査透明性レポート
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/USER-GUIDE.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/adr/0011-skill-surface-budget-module.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/RELEASE-v1.42.1.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/COMMANDS.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/ARCHITECTURE.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/CONFIGURATION.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/CLI-TOOLS.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/docs/FEATURES.md
- https://github.com/open-gsd/get-shit-done-redux/blob/next/CHANGELOG.md
