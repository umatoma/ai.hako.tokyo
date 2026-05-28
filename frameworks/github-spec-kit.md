---
title: GitHub Spec Kit — Spec-Driven Development ツールキット
updated: 2026-05-28
tags: [github, spec-kit, spec-driven-development, sdd, cli, ai-coding-agents, methodology]
related_sources:
  - sources/github/spec-kit/readme.md
  - sources/github/spec-kit/spec-driven.md
  - sources/github/spec-kit/docs-home.md
  - sources/github/spec-kit/installation.md
  - sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md
---

# GitHub Spec Kit — Spec-Driven Development ツールキット

GitHub が 2025-09-02 にオープンソース公開した、**Spec-Driven Development (SDD; 仕様駆動開発)** のためのツールキット。「仕様を執行可能 (executable) な成果物にし、コードはその表現とする」という思想を、`specify` CLI と 4 つのスラッシュコマンドで具体化する。Claude Code、GitHub Copilot、Gemini CLI など 30 以上の AI コーディングエージェントから使える（取得時点 [`docs-home.md`](../sources/github/spec-kit/docs-home.md)）。

このノートは GitHub 公式の 5 ソース（README、`spec-driven.md`、ドキュメントトップ、Installation Guide、発表ブログ）から、**どう動くか・何を解こうとしているか・他のアプローチと並べるとどこか**を整理する。

## 中核となる主張: 力関係の逆転

伝統的には **コード = source of truth**、仕様は捨てられる足場だった。Spec Kit は **意図 = source of truth** に逆転させる。

> "We're moving from 'code is the source of truth' to 'intent is the source of truth.'"
> 「我々は『コードが真実の源泉』から『意図が真実の源泉』へ移行している。」
> — [発表ブログ](../sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md)

これを成立させているのが「AI が仕様を実行可能にする」という前提。仕様がコードを生成するから、仕様が「何が作られるか」を決定する ([`spec-driven.md`](../sources/github/spec-kit/spec-driven.md))。

## 4 フェーズワークフロー (Spec → Plan → Tasks → Implement)

| フェーズ | コマンド | やること | 焦点 |
|---|---|---|---|
| 1. **Specify** | `/speckit.specify` | 何を、なぜ作るかを記述。ユーザージャーニーと体験。技術スタックには触れない | What / Why |
| 2. **Plan** | `/speckit.plan` | 技術スタック・アーキテクチャ・制約を与える。社内標準があればここで | How（技術判断） |
| 3. **Tasks** | `/speckit.tasks` | 仕様と計画から、隔離して実装・テストできる小さなタスクへ分解。`[P]` で並行可能を示す | 実行可能な分解 |
| 4. **Implement** | `/speckit.implement` | タスクを依存順に実行。TDD 構造を尊重。エラーは適切に処理 | 動くコード |

各フェーズに**明示的なチェックポイント**があり、現フェーズが検証されるまで次へ進まない。あなたの役割は「舵取り＋検証」。AI が成果物を生成し、人間が正しさを保証する ([発表ブログ](../sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md))。

### 補助コマンド

| コマンド | 用途 | 推奨タイミング |
|---|---|---|
| `/speckit.constitution` | プロジェクトの統治原則を作成・更新 | プロジェクト最初 |
| `/speckit.clarify` | 仕様の曖昧箇所を構造化された質問で詰める | `/speckit.plan` の前（推奨） |
| `/speckit.analyze` | 成果物横断の一貫性・カバレッジ分析 | `/speckit.tasks` の後、`/speckit.implement` の前 |
| `/speckit.checklist` | 「要件の単体テスト」となる品質チェックリストを生成 | 仕様レビュー時 |
| `/speckit.taskstoissues` | タスクを GitHub Issue に変換 | チームで実行を分担するとき |

## コンスティチューション (Constitution) — 不変原則による規律

`.specify/memory/constitution.md` に「9 つの条項」を置き、計画・実装フェーズで強制する。`spec-driven.md` で明示されている主要条項:

| 条項 | 内容 | 強制方法 |
|---|---|---|
| I. **ライブラリファースト** | すべての機能は独立したライブラリとして始まる | 実装計画テンプレート |
| II. **CLI インターフェース義務** | すべてのライブラリは stdin/stdout（JSON 可）の CLI で機能を公開 | 観測可能性とテスト容易性の強制 |
| III. **テストファースト** | テストが書かれ承認され Red 確認されるまで実装コードを書かない | 「NON-NEGOTIABLE」と明記 |
| VII. **単純性ゲート** | プロジェクト数 ≤ 3、将来対応を入れない | 計画前ゲート |
| VIII. **アンチ抽象化** | フレームワークを直接使う、モデル表現は単一 | 計画前ゲート |
| IX. **インテグレーションファーストテスト** | モックより実 DB、契約テストは実装より前 | 計画前ゲート |

ゲートを通せない場合は「Complexity Tracking」セクションに正当化を書かないと次へ進めない仕組み。LLM が安易に複雑さを足すのを阻む装置として設計されている ([`spec-driven.md`](../sources/github/spec-kit/spec-driven.md))。

## テンプレートが LLM をどう「制約」するか

`spec-driven.md` は、テンプレートを「洗練されたプロンプト」として位置付け、LLM の典型的失敗モードを次のように抑止する:

1. **過早な実装詳細を防ぐ** — 仕様テンプレートで「WHAT/WHY のみ、HOW（技術スタック）を書かない」を強制
2. **明示的な不確実性マーカー** — `[NEEDS CLARIFICATION: specific question]` を強制し、推測を可視化
3. **チェックリスト = 仕様の単体テスト** — 完全性・テスト可能性・明確さを LLM 自身に自己レビューさせる
4. **ゲートで複雑さに説明責任** — 例外は「Complexity Tracking」に書かないと通れない
5. **階層的詳細管理** — 詳細は `implementation-details/` に追い出し、計画書は読みやすく保つ
6. **テストファースト思考** — `contracts/` → contract → integration → e2e → unit → 実装、の順序
7. **推測機能の排除** — 「あったらいいね (might need)」は禁止

これらの「複合効果」として、生成される仕様は完全 / 明確 / テスト可能 / 保守可能 / 実装可能になる。

## カスタマイズ階層: Extensions / Presets / Local Overrides

Spec Kit は自社・自プロジェクトの事情に合わせて、4 段の優先度スタックで挙動を調整できる:

| 優先度 | 種類 | 場所 | 何ができるか |
|---|---|---|---|
| ⬆ 1 | プロジェクトローカル上書き | `.specify/templates/overrides/` | 1 プロジェクト限定の臨時調整 |
| 2 | プリセット (Presets) | `.specify/presets/templates/` | ワークフローの「やり方」をカスタマイズ（コマンドの中身を上書き） |
| 3 | 拡張 (Extensions) | `.specify/extensions/templates/` | 新しいコマンド・能力を追加 |
| ⬇ 4 | Spec Kit Core | `.specify/templates/` | 組み込み SDD コマンド・テンプレート |

判断軸（README より）:

| ゴール | 使うもの |
|---|---|
| 新コマンド・新ワークフロー追加 | Extension |
| 仕様・計画・タスクの形式をカスタマイズ | Preset |
| 外部ツール・サービス連携 | Extension |
| 組織標準・規制標準の強制 | Preset |

取得時点でコミュニティ拡張 105 / プリセット 22 / 統合 30。代替プロセスとして AIDE（7 ステップ AI 駆動）、Canon（ベースライン駆動）、Product Forge（プロダクトマネジメント指向）、FX→.NET、MAQA などが流通している ([docs-home](../sources/github/spec-kit/docs-home.md))。

## 特に効く 3 つの場面

[発表ブログ](../sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md) が挙げている適用シナリオ:

1. **グリーンフィールド (0 → 1)**: 即コーディングではなく、仕様と計画の先行投資で「汎用解」ではなく「意図した解」を作らせる。
2. **既存システムへの機能追加 (N → N+1)**: 既存システムとの相互作用を仕様で強制的に明確化。計画にアーキテクチャ制約を符号化し、新コードが「ネイティブ」に感じられるようにする。**最も強力**な場面。
3. **レガシー近代化**: 当初の意図が失われたシステムでも、ビジネスロジックを新しい仕様で再表現し、技術負債を引き継がずに再構築。

## インストール（要点）

[Installation Guide](../sources/github/spec-kit/installation.md) より要約。

```sh
# 永続インストール（推奨）— vX.Y.Z は Releases の最新タグ
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z

# プロジェクト初期化
specify init my-project --integration claude   # Claude Code 連携の場合
# 他: copilot / gemini / codex / codebuddy / pi / ...

# 検証
specify version
```

前提: Python 3.11+, Git, [uv](https://docs.astral.sh/uv/) 推奨。Linux / macOS / Windows（PowerShell 自動化スクリプトもサポート）。

## 典型的な失敗 / アンチパターン

README と発表ブログから読み取れる落とし穴:

- **仕様フェーズで技術スタックを書く** — 仕様テンプレートが明示的に阻むが、人間が誘導してしまいがち。`/speckit.specify` では WHAT/WHY のみに留める。
- **明確化を飛ばして `/speckit.plan` に進む** — `/speckit.clarify` を挟む推奨順序を破ると、計画が誤った仮定で進む。
- **過剰設計 (over-engineering)** — README 自身が「Claude Code can be over-eager」と注意喚起。コンスティチューションの単純性ゲートと「Complexity Tracking」で強制される。
- **CLI ログだけ見て実装完了とする** — `/speckit.implement` 後はブラウザコンソールエラー等も確認し、エージェントへフィードバック。

## 関連ノート

- [`topics/software-development/ai-sdlc-methodologies-compared.md`](../topics/software-development/ai-sdlc-methodologies-compared.md) — **Spec Kit / AI-DLC / GSD の横断比較表**（唯一の置き場）
- [`aws-ai-dlc.md`](aws-ai-dlc.md) — もう一つの SDD/SDLC 再構想メソドロジー（適応的 3 フェーズ + Mob 様式）
- [`open-gsd-get-shit-done-redux.md`](open-gsd-get-shit-done-redux.md) — コンテキスト腐敗対策と並列波実行
- [`anthropic-claude-code.md`](anthropic-claude-code.md) — Claude Code 全般。Spec Kit は Claude Code から `/speckit.*` で呼べる
- [`topics/software-development/ai-native-startup-lifecycle.md`](../topics/software-development/ai-native-startup-lifecycle.md) — Idea / MVP / Launch / Scale の 4 段階モデル。Spec Kit は特に MVP〜Launch のスコープ規律と相性が良い
- [`playbooks/software-development/01-claude-codeを導入する.md`](../playbooks/software-development/01-claude-codeを導入する.md) — Claude Code 導入手順

## 拡張余地 / 今後の予定

- 取得時点で**実プロジェクトでの使用感**を [`playbooks/software-development/`](../playbooks/software-development/) に落とし込めていない。導入ステップを `03-spec-kit-を導入する.md` 等で追加する候補。
- コミュニティ拡張・プリセット（105 / 22）の中で有用なものは別途キュレーション対象。
- Constitution の「9 条項」のうち、原文に詳細記述があるのは I / II / III / VII / VIII / IX のみ（IV〜VI は本文では番号触れず）。原典で追補される可能性があるので `updated` を見直すこと。
