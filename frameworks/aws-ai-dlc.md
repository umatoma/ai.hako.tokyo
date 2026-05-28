---
title: AWS AI-DLC — AI-Driven Development Life Cycle
updated: 2026-05-28
tags: [aws, ai-dlc, methodology, amazon-q-developer, kiro, workflow-scaffolds, human-in-the-loop]
related_sources:
  - sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md
  - sources/aws/ai-dlc/2025-11-29-open-sourcing-adaptive-workflows.md
  - sources/aws/ai-dlc/2025-11-29-building-with-ai-dlc-using-amazon-q-developer.md
  - sources/aws/ai-dlc/aidlc-workflows-readme.md
---

# AWS AI-DLC — AI-Driven Development Life Cycle

AWS（主に Principal Solutions Architect の Raja SP のチーム）が提唱する、AI を「アシスタント」ではなく**中心的協力者**として位置付ける開発メソドロジー。2025-07-31 に[発表記事](../sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md)で公開され、2025-11-29 に [Amazon Q Rules / Kiro Steering Files として](../sources/aws/ai-dlc/2025-11-29-open-sourcing-adaptive-workflows.md) MIT-0 ライセンスでオープンソース化された (`awslabs/aidlc-workflows`)。

このノートは 4 つの AWS 公式ソース（発表ブログ、OSS 化ブログ、Q Developer ウォークスルー、リポジトリ README）から、**設計思想・3 フェーズの構造・適応の仕組み・GitHub Spec Kit との位置関係**を整理する。

## 2 つの設計次元

[発表記事](../sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md)で AI-DLC は次の 2 軸の上に立つと宣言される:

| 次元 | 内容 | 帰結 |
|---|---|---|
| **AI Powered Execution with Human Oversight** | AI が計画を作り、明確化を求め、重要判断を人間に委ねる | プロセスは AI 主導、判断は人間 |
| **Dynamic Team Collaboration** | AI が定型を処理する間、チームはリアルタイム協業に集中（Mob Elaboration / Mob Construction） | 個人作業からチーム作業への重心移動 |

> "AI Powered Execution with Human Oversight: AI systematically creates detailed work plans, actively seeks clarification and guidance, and defers critical decisions to humans."

## 3 フェーズ適応型ワークフロー

[リポジトリ README](../sources/aws/ai-dlc/aidlc-workflows-readme.md) と [Q Developer ウォークスルー](../sources/aws/ai-dlc/2025-11-29-building-with-ai-dlc-using-amazon-q-developer.md) より:

| フェーズ | 決めること | 主なステージ | 例: 単純バグ修正の場合 |
|---|---|---|---|
| 🔵 **Inception** | WHAT / WHY | Workspace Detection → Requirements Analysis → Workflow Planning | Workspace Detection のみで Construction に直行することも |
| 🟢 **Construction** | HOW | Code Generation Planning → Code Generation → Build and Test | Code Generation のみで完了することも |
| 🟡 **Operations** | デプロイと監視 (将来) | Deployment / Monitoring | スキップされることが多い |

**ワークフローはリクエスト・コードベース・複雑さを分析して、必要なステージだけを動的に選ぶ**。これが Spec Kit との大きな違い（Spec Kit は Constitution + 4 フェーズが基本固定で、Presets/Extensions で「上書き」する）。

### 1 サイクルのインタラクションパターン

1. 人間がタスク記述を提供
2. AI が計画を作り、明確化を求める
3. 人間が明確化を提供
4. AI が計画を洗練
5. 人間が計画を承認
6. AI が計画を実行
7. 人間が結果を検証

このサイクルが各ステージで繰り返される。承認なしには進めない構造になっており、「[`Mob Elaboration`](../sources/aws/ai-dlc/2025-11-29-open-sourcing-adaptive-workflows.md) / Mob Construction」と呼ばれる。

## 3 つの解こうとしている課題

[OSS 化ブログ](../sources/aws/ai-dlc/2025-11-29-open-sourcing-adaptive-workflows.md) が AI-DLC の正当化として挙げる 3 つの課題:

| 課題 | 既存ツールの傾向 | AI-DLC の応答 |
|---|---|---|
| 画一的ワークフロー | スコープに関係なく同一プロセスを強制 | **原則 10「No Hard-Wired, Opinionated SDLC Workflows」**。Level 1 プランを AI が経路意図から推薦 |
| 各段階の深さの欠如 | 過剰設計 or 厳密さ不足の二択 | 広さ（段階選択）と深さ（強度）の両方を適応 |
| 過剰自動化 | 「process atrophy」（プロセス萎縮）を生む | 全段階で human-in-the-loop と監査トレイルを強制 |

## 用語の変更（Agile からの再構想）

[発表記事](../sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md)で AI-DLC は Agile の用語を意図的に置き換える:

| 伝統的 Agile | AI-DLC |
|---|---|
| Sprints（週単位） | **Bolts**（時間・日単位の短期集中サイクル） |
| Epics | **Units of Work** |
| Backlog grooming | （Mob Elaboration に統合） |
| Standup | （リアルタイム協業の中で常時実施） |

この用語シフトは「速度と継続的提供」を強調するためのもの。

## 信条 (Tenets)

リポジトリ README で明示されているコア信条:

1. **重複なし (No duplication)** — 真実の源は一箇所、必要なら生成
2. **メソドロジーファースト** — AI-DLC はツールではなくメソドロジー。何もインストールせずに始められるべき
3. **再現可能 (Reproducible)** — 異なる LLM でも類似の結果が出るほど明確なルール
4. **非依存 (Agnostic)** — 任意の IDE、エージェント、モデルで動く
5. **Human in the loop** — 重要判断は明示的なユーザー確認が必須

## 実装手段: Rules / Steering / AGENTS.md

AI-DLC は専用ツールを配らず、**既存のコーディングエージェントのルール機構を使う「ワークフロー・スキャフォールド (workflow scaffolds)」**として提供される。同じルール本体 (`aws-aidlc-rules/core-workflow.md`) を各エージェントの慣習に従って配置する:

| エージェント | 配置先 | 仕組み |
|---|---|---|
| Kiro / Kiro CLI | `.kiro/steering/aws-aidlc-rules/` | Steering Files |
| Amazon Q Developer | `.amazonq/rules/aws-aidlc-rules/` | Amazon Q Rules（一次提供形態） |
| Cursor | `.cursor/rules/ai-dlc-workflow.mdc` | Project Rules（推奨）or AGENTS.md |
| Cline | `.clinerules/core-workflow.md` | Cline Rules |
| Claude Code | プロジェクトルートの `CLAUDE.md` | プロジェクトメモリ（Claude Code 既存の規約をそのまま使う） |
| GitHub Copilot | `.github/copilot-instructions.md` | Custom Instructions |
| OpenAI Codex | `AGENTS.md` | AGENTS.md 規約 |

詳細ルール (`aws-aidlc-rule-details/`) は必要時にだけロードされ、トークン消費を最適化する設計。

> 「`aws-aidlc-rules/core-workflow.md` を主要文脈とし、詳細なフェーズ・ステージレベルルールは `aws-aidlc-rule-details` に格納して動的にロード。任意時点で必要な情報だけを文脈に保ち、トークン消費を最適化する。」 — [Q Developer ウォークスルー](../sources/aws/ai-dlc/2025-11-29-building-with-ai-dlc-using-amazon-q-developer.md)

## 生成される成果物

ウォークスルーが示すように、AI-DLC は `aidlc-docs/` ディレクトリにすべての成果物を保存する:

- `aidlc-state.md` — エラー復旧とセッション継続のための進捗追跡
- `audit.md` — ユーザープロンプトと応答の監査トレイル
- `requirement-verification-questions.md` — 明確化質問（多肢選択 + Other）
- `requirements.md` — Intent Analysis Summary、User Request、Functional Requirements
- `execution-plan.md` — 推奨ステージ、スキップステージ、リスク、ワークフロー図
- `{unit-name}-code-generation-plan.md` — 番号付き実装計画（チェックボックス付き）
- ビルド・テスト指示ファイル

監査トレイルと state ファイルが**セッションをまたいだ継続**を可能にし、Spec Kit の `.specify/memory/` と類似の役割を果たす。

## 拡張 (Extensions) システム

リポジトリ README の Extensions システム:

- 各拡張 = ルールファイル + Opt-in ファイルのペア（`security-baseline.md` + `security-baseline.opt-in.md`）
- ワークフロー開始時に `*.opt-in.md` をスキャン → Requirements Analysis で提示 → opt-in されたものだけルール本体をロード
- 一度有効になるとルールは**ブロッキング制約**: 各ステージで検証通過が必須
- 命名規約: `## Rule <PREFIX-NN>: <Title>`（例: `COMPLIANCE-01`）。Rule / Verification の 2 セクション構成
- 組み込み: `security/baseline/`, `testing/property-based/`

セキュリティ拡張は「方向性参照」と注記されており、各組織で自社ルールを構築・テストすることが推奨されている。

## 補助ツール

リポジトリ `scripts/` 配下の 2 つ:

| ツール | 用途 |
|---|---|
| **AIDLC Evaluator** | ワークフロー変更の自動回帰テスト基盤。Golden Test Cases、Semantic Evaluation、Code Evaluation（lint/security/重複検出）、NFR Evaluation（トークン使用量・実行時間・モデル間一貫性）、CI/CD 統合 |
| **AIDLC Design Reviewer**（実験的） | AWS Bedrock 経由で Claude を使い、生成された設計成果物を 3 種の特化エージェント（Critique、Alternatives、Gap Analysis）でレビュー。CLI 版と Claude Code フック版がある |

## 他メソドロジーとの比較

Spec Kit / GSD との横断比較は [`topics/software-development/ai-sdlc-methodologies-compared.md`](../topics/software-development/ai-sdlc-methodologies-compared.md) に集約してある。使い分けの目安・共通アンチパターン・組み合わせ可能性もそちらを参照。

## 典型的な失敗 / アンチパターン

ソース全体から読み取れる注意点:

- **「Using AI-DLC, …」を付け忘れる** — README より、これがワークフロー有効化のトリガー
- **計画フェーズで承認を急ぐ** — 明確化質問に向き合わず承認すると、矛盾を含んだ要件のまま Construction に進む
- **過剰自動化に流れる** — `process atrophy` は OSS 化ブログが名指しで警告
- **拡張の本番投入時にセキュリティルールをそのまま使う** — README 自身が「方向性参照」と明示。組織側でカスタマイズ＋テストが必須
- **`aidlc-docs/` を .gitignore してしまう** — 監査トレイル・state ファイルが消えてセッション継続できなくなる（README はコミットを推奨）

## 関連ノート

- [`topics/software-development/ai-sdlc-methodologies-compared.md`](../topics/software-development/ai-sdlc-methodologies-compared.md) — **Spec Kit / AI-DLC / GSD の横断比較表**（唯一の置き場）
- [`github-spec-kit.md`](github-spec-kit.md) — もう一つの SDD/SDLC 再構想メソドロジー
- [`open-gsd-get-shit-done-redux.md`](open-gsd-get-shit-done-redux.md) — コンテキスト腐敗対策と並列波実行
- [`anthropic-claude-code.md`](anthropic-claude-code.md) — Claude Code は AI-DLC の対応エージェントの一つ。プロジェクトルートに `CLAUDE.md` を置く規約はそのまま使える
- [`topics/software-development/ai-native-startup-lifecycle.md`](../topics/software-development/ai-native-startup-lifecycle.md) — Idea/MVP/Launch/Scale の段階別考え方。AI-DLC の Bolts と組み合わせるのが筋

## 拡張余地 / 今後の予定

- Method Definition Paper (`prod.d13rzhkk8cj2z0.amplifyapp.com`) はまだ取り込んでいない。原典なので [`sources/aws/ai-dlc/docs/`](../sources/aws/ai-dlc/) 配下に追加候補
- **9 原則 (No Hard-Wired, Opinionated SDLC Workflows) のうち取得できているのは 10 番だけ**。残り 9 原則は OSS 化ブログ本文には現れず、Method Definition Paper にあると思われる
- 実プロジェクトでの導入手順は `playbooks/software-development/` への落とし込みが未完了
- [topics/software-development/](../topics/software-development/) に「AI 時代の SDLC メソドロジー比較」ノートを起こすと、Spec Kit / AI-DLC を並べた整理が継続的に育てやすい
