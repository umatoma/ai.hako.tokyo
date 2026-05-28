---
title: GSD (Get Shit Done Redux) — マルチエージェント仕様駆動システム
updated: 2026-05-28
tags: [gsd, open-gsd, get-shit-done-redux, spec-driven-development, context-engineering, multi-agent, claude-code, parallel-execution]
related_sources:
  - sources/open-gsd/get-shit-done-redux/readme.md
---

# GSD (Get Shit Done Redux) — マルチエージェント仕様駆動システム

open-gsd チームが保守するオープンソース（MIT）の SDD/コンテキストエンジニアリングシステム。Claude Code を主軸に、OpenCode / Gemini CLI / Kilo / Codex / Copilot / Cursor / Windsurf など 15 ランタイム対応。自らを「**軽量なメタプロンプティング・コンテキストエンジニアリング・仕様駆動開発システム**」と位置付け、目標は「**コンテキスト腐敗 (context rot)** ― AI が文脈窓を埋めるにつれて起こる品質低下 ― を解決すること」。

このノートは [公式 README](../sources/open-gsd/get-shit-done-redux/readme.md) を起点に、**何を解こうとしているか・GSD ループの 6 ステップ・Spec Kit / AI-DLC との違い**を整理する。

## 背景: 「Redux」が指すもの

README 冒頭の「Project Continuity Notice」によれば、GSD は元々別の人物が始めたプロジェクトだったが、2026 年 5 月に「**所有権と信頼の懸念（meme-coin の rug-pull 事件を含む）**」を受けて、open-gsd チームがフォークして保守する形に移行した。

- 旧アップストリームは open-gsd の統制下にない
- 公式パッケージは `@opengsd/get-shit-done-redux` と `@opengsd/gsd-sdk` のみ
- 監査ステータスは [Discussion #119](https://github.com/open-gsd/get-shit-done-redux/discussions/119)、移行アナウンスは [#109](https://github.com/open-gsd/get-shit-done-redux/discussions/109) で公開

このため、**「GSD = open-gsd/get-shit-done-redux」を指すとき**は MIT ライセンスのコミュニティ保守版を意味する。旧パッケージ名（`@speedwise/*` など他人保有のもの）は使わないことが推奨されている。

## 6 コマンドの中核ループ

[README](../sources/open-gsd/get-shit-done-redux/readme.md) より、「ループは 6 コマンド、各コマンドは正確に 1 つのことだけをする」。

| # | コマンド | 1 行説明 | 何が起きるか |
|---|---|---|---|
| 1 | `/gsd-new-project` | 初期化 | 質問 → リサーチ → 要件 → ロードマップ |
| 2 | `/gsd-discuss-phase [N]` | 議論（任意） | 計画前に「あなたが思う通り」の判断を捕まえる |
| 3 | `/gsd-plan-phase [N]` | 計画 | リサーチ → 計画 → 検証 のループ（小さく fresh context window で実行できる単位に） |
| 4 | `/gsd-execute-phase <N>` | 実行 | 並列の波 (waves) でサブエージェントが実行。各タスクが**アトミックコミット** |
| 5 | `/gsd-verify-work [N]` | 検証 | 手動受け入れテスト＋自動診断＋修正計画。デバッグは「再 execute」で行う |
| 6 | `/gsd-ship [N]` | 出荷 | 検証済みフェーズから PR 作成 → `/gsd-complete-milestone` → `/gsd-new-milestone` |

既存コードに導入する場合は、ループ前に `/gsd-map-codebase` でスタック・アーキテクチャ・慣習を分析する。

### Discuss フェーズの位置付け

GSD 独自で目を引くのは Step 2「Discuss」の存在:

> 「ロードマップは 1 フェーズに 1 文しかない。それでは『**あなた**が思い描いた通り』に作るには足りない。ディスカスは計画を始める前にあなたの判断を捕まえる: レイアウト、API の形、エラーハンドリング、データ構造 ― 特定フェーズに存在する任意のグレー領域について。」

スキップすれば「妥当なデフォルト」、使えば「あなたのビジョン」になる ― という設計。Spec Kit の `/speckit.clarify` に近い役割だが、**フェーズ単位**で繰り返し走る点が特徴。

## なぜ効くか — 3 つの問題と GSD の答え

| 問題 | GSD の対処 |
|---|---|
| **コンテキスト肥大化** | 重作業をサブエージェントの新鮮な 200k トークン文脈で行う。リサーチャー・プランナー・エグゼキューターはそれぞれ fresh start。メイン文脈は 30–40% に保つ |
| **共有メモリの欠如** | セッション境界を越えて生き残る構造化成果物: `PROJECT.md` / `REQUIREMENTS.md` / `ROADMAP.md` / `STATE.md` / `CONTEXT.md` |
| **検証の欠如** | "走る" コードは "動く" コードではない。Verify ステップが診断と修正計画を生成し、修正は手動デバッグせず再 execute |

## アーキテクチャ的特徴

README が明示する技術的選択:

- **並列波実行 (Parallel Waves)** — 独立した計画を同時実行。`parallelization.enabled` で制御
- **アトミックコミット** — 各タスクが独立したコミットを生む（事後ロールバックを容易に）
- **モデルプロファイル** — `quality` / `balanced` / `budget` をエージェント単位で選択可能（README の Configuration セクション）
- **ランタイム表面制御** — `/gsd:surface` で再インストールせずスキルクラスタを実行時にオン/オフ
- **インストールプロファイル** — `core`（6 スキル）、`standard`（コア＋フェーズ管理）、デフォルトのフル。プロファイルは合成可能 (`--profile=core,audit`)
- **パッケージ正当性チェック** — リサーチ・計画・実行に組み込み。未検証パッケージは人間チェックポイント、失敗インストールで類似名代替は試みない
- **fallow による構造レビュー（任意）** — `code_quality.fallow.enabled` で `/gsd-code-review` にプレパスを追加

### 永続成果物（`.planning/` 配下）

| ファイル | 役割 |
|---|---|
| `PROJECT.md` | ビジョン |
| `REQUIREMENTS.md` | スコープ |
| `ROADMAP.md` | 向かう先 |
| `STATE.md` | 現位置と判断 |
| `CONTEXT.md` | フェーズごとの実装判断 |
| `.planning/config.json` | 設定（mode, model profiles, workflow toggles, parallelization） |
| `.planning/phases/<phase>/FALLOW.json` | （任意）構造レビュー結果 |

Spec Kit の `.specify/memory/`、AI-DLC の `aidlc-docs/` に相当するレイヤー。

## クロスランタイム互換性の落とし穴

README が明示している重要な実装事情:

- リポジトリの `agents/` と `commands/` は **Claude Code フォーマット** がソース
- インストーラー (`npx @opengsd/get-shit-done-redux@latest`) が各ターゲットランタイム向けに frontmatter を変換する
- 例: OpenCode は `color` を固定セットの値で要求し `tools:` を拒否 → インストーラー関数 `convertClaudeToOpencodeFrontmatter`（`bin/install.js`）が処理
- **手動コピーは禁忌** — 直接 `~/.config/opencode/agents` などに置くと変換が走らず schema 検証エラーになる
- Node.js なし環境（Windows + OpenCode）の場合は `docs/USER-GUIDE.md#manual-install--no-nodejs-setup`

## Claude Code との結合

GSD は Claude Code を主軸に作られている。README は次を推奨している:

```sh
claude --dangerously-skip-permissions
```

> 「GSD は摩擦のない自動化のために作られている。Skip-permissions は意図された実行方法。」

インストール先は `~/.claude/skills/gsd-*/`。コンテナや Docker では `CLAUDE_CONFIG_DIR` を設定してチルダ展開問題を回避する必要がある。

## 他メソドロジーとの比較

Spec Kit / AI-DLC との横断比較は [`topics/software-development/ai-sdlc-methodologies-compared.md`](../topics/software-development/ai-sdlc-methodologies-compared.md) に集約してある。使い分けの目安・共通アンチパターン・組み合わせ可能性もそちらを参照。

## 典型的な失敗 / アンチパターン

README から読み取れる注意点:

- **手動でファイルをコピーする** — 変換が走らず schema エラー。必ずインストーラー経由
- **旧パッケージ名を使う** — `@speedwise/*` 系は open-gsd 統制下にない。`@opengsd/*` を使う
- **`/gsd-discuss-phase` をスキップして「妥当なデフォルト」を望む** — それで動くが「あなたのビジョン」にはならない
- **Codex CLI < 0.130.0** — 追加ルート探索が残っており、`gsd-*` の重複表示が起きうる
- **コンテナで `CLAUDE_CONFIG_DIR` を設定し忘れる** — チルダ展開でインストール先が壊れる
- **fallow を `cargo install` で入れたが古いバージョン** — JSON スキーマ不一致で「無音で 0 件出力」を出すことがある。v2.70+ が必要

## 関連ノート

- [`topics/software-development/ai-sdlc-methodologies-compared.md`](../topics/software-development/ai-sdlc-methodologies-compared.md) — **Spec Kit / AI-DLC / GSD の横断比較表**（唯一の置き場）
- [`github-spec-kit.md`](github-spec-kit.md) — もう一つの SDD ツールキット
- [`aws-ai-dlc.md`](aws-ai-dlc.md) — AWS の SDLC 再構想メソドロジー
- [`anthropic-claude-code.md`](anthropic-claude-code.md) — GSD は Claude Code 主軸。`--dangerously-skip-permissions` の扱いはここでも触れている

## 拡張余地 / 今後の予定

- **`docs/ARCHITECTURE.md` は未取り込み**。マルチエージェントオーケストレーションの詳細はここにある。次の取り込み候補として有力
- **`docs/USER-GUIDE.md` / `docs/COMMANDS.md` も未取り込み**。実プロジェクトで導入するときに必要
- README には言及がないが、`gsd-sdk` (`@opengsd/gsd-sdk`) のプログラマティック API も別途整理価値あり (`docs/CLI-TOOLS.md`)
- `playbooks/software-development/` に「GSD で既存リポを並列波実行に乗せる」レシピを残すと、Spec Kit と並ぶ実用ノートになる
- **信頼性メモ**: コミュニティ保守＋過去にエコシステムで rug-pull 事件があった経緯から、本番採用前に [Discussion #119](https://github.com/open-gsd/get-shit-done-redux/discussions/119) の監査レポートを各自で確認すること
