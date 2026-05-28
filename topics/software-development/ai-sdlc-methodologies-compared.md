---
title: AI 時代の SDLC メソドロジー比較 — Spec Kit / AI-DLC / GSD
updated: 2026-05-28
tags: [sdd, sdlc, spec-driven-development, methodology-comparison, github-spec-kit, aws-ai-dlc, gsd, context-engineering]
related_sources:
  - sources/github/spec-kit/readme.md
  - sources/github/spec-kit/spec-driven.md
  - sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md
  - sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md
  - sources/aws/ai-dlc/2025-11-29-open-sourcing-adaptive-workflows.md
  - sources/aws/ai-dlc/aidlc-workflows-readme.md
  - sources/open-gsd/get-shit-done-redux/readme.md
---

# AI 時代の SDLC メソドロジー比較 — Spec Kit / AI-DLC / GSD

「コーディングエージェントが強力になった今、何を中心に据え、どう統制し、人間と AI のどこに境界を引くか」を、別々の角度から答える 3 つのメソドロジーが 2025–2026 年に出揃った。このノートはそれらをベンダー横断で並べる**唯一の比較表の置き場**。各メソドロジー自体の詳細は frameworks/ の専用ノートに残す。

| メソドロジー | 提供元 | 公開 | 専用ノート |
|---|---|---|---|
| **GitHub Spec Kit** | GitHub | 2025-09-02 | [`frameworks/github-spec-kit.md`](../../frameworks/github-spec-kit.md) |
| **AWS AI-DLC** | AWS（Raja SP のチーム） | 2025-07-31（OSS 化 2025-11-29） | [`frameworks/aws-ai-dlc.md`](../../frameworks/aws-ai-dlc.md) |
| **GSD (Get Shit Done Redux)** | open-gsd（コミュニティ） | 2026-05（Redux 移行） | [`frameworks/open-gsd-get-shit-done-redux.md`](../../frameworks/open-gsd-get-shit-done-redux.md) |

## 共通する 3 つの問題意識

3 つのメソドロジーは表現は違うが、同じ問題に答えようとしている:

1. **vibe coding ではミッションクリティカルに耐えない** — Spec Kit / AI-DLC が明示。GSD は "context rot" の表現で同じ問題を指す。
2. **コードを真実の源にすると、意図と実装がずれていく** — 仕様 / 計画 / 文脈を別レイヤーで持つことで、再生成可能なシステムを目指す。
3. **AI を「アシスタント」のままにすると能力を引き出せない** — AI を中心または主軸に据え、人間は「重要判断」「検証」に役割を移す。

## 中心概念の違い（哲学レベル）

| メソドロジー | 中心に据えるもの | 出典の一言 |
|---|---|---|
| Spec Kit | **仕様 (specification) = source of truth** | "intent is the source of truth" — [Spec Kit 発表ブログ](../../sources/github/spec-kit/2025-09-02-spec-driven-development-announcement.md) |
| AI-DLC | **AI = 中心的協力者 (central collaborator)** | "AI must be positioned as a central collaborator and teammate" — [AI-DLC 発表記事](../../sources/aws/ai-dlc/2025-07-31-ai-driven-development-life-cycle.md) |
| GSD | **コンテキスト = 統制対象** | "Solves context rot — the quality degradation that happens as your AI fills its context window" — [GSD README](../../sources/open-gsd/get-shit-done-redux/readme.md) |

Spec Kit は「**何を作るか (intent)**」、AI-DLC は「**誰がどう作るか (AI＋Mob)**」、GSD は「**どこで考えるか (どの文脈窓で何を持つか)**」に切り口がある ― 3 者が直交している点が、組み合わせ可能性を生んでいる。

## 全体比較表

| 観点 | GitHub Spec Kit | AWS AI-DLC | GSD (open-gsd) |
|---|---|---|---|
| **メソドロジー / 実装の重心** | 仕様を中心に据える方法論 | 適応的に AI が主導する SDLC 全体 | コンテキスト腐敗を解く実装システム |
| **配布形態** | `specify` CLI + リポ内テンプレート | 既存エージェントの Rules/Steering に重ねるスキャフォールド（CLI なし） | npm パッケージ `@opengsd/*` + 各ランタイム向けの自動変換 |
| **フェーズ構造** | 固定 4 段（Spec → Plan → Tasks → Implement） | 適応 3 段（Inception → Construction → Operations）。ステージは動的選択 | 6 コマンドのループ（Init/Discuss/Plan/Execute/Verify/Ship） |
| **規律強制** | コンスティチューション 9 条項 + テンプレートゲート | 信条 5 つ + 拡張のブロッキング検証 | サブエージェント分離 + アトミックコミット + 検証エージェント |
| **協業様式** | 個人＋ AI の対話（チーム言及はある） | **Mob Elaboration / Mob Construction**（チーム全員で精緻化） | 単独ビルダー〜小規模チーム向け（README 自己定義） |
| **並列実行** | タスク内 `[P]` マーキング | 拡張で表現可能 | **第一級**: 並列波 (waves) + parallelization 設定が中心機能 |
| **コンテキスト管理** | テンプレート階層化、`.specify/templates/overrides/` | 詳細ルールの動的ロード、`aws-aidlc-rule-details/` | サブエージェントの fresh 200k 文脈、メイン文脈 30–40% を維持 |
| **永続成果物の置き場** | `.specify/memory/constitution.md`、`specs/<branch>/spec.md` ほか | `aidlc-docs/`（`state.md`, `audit.md`, `requirements.md`, `execution-plan.md` ほか） | `.planning/`（`PROJECT.md`, `REQUIREMENTS.md`, `ROADMAP.md`, `STATE.md`, `CONTEXT.md`） |
| **時間単位語彙** | Phase（明示語彙なし） | **Bolts**（時間・日単位）が Sprints を置換 | Milestone と Phase（明示語彙なし） |
| **対応エージェント** | 30 以上 | Kiro / Amazon Q / Cursor / Cline / Claude Code / Copilot / Codex の 7 系 | 15 ランタイム（Claude Code/OpenCode/Gemini CLI/Kilo/Codex/Copilot/Cursor/Windsurf ほか） |
| **拡張機構** | Extensions / Presets / Local Overrides（4 段優先度） | Extensions（opt-in 式、Rule/Verification セクション規約、ブロッキング検証） | プロファイル合成 + `/gsd:surface` で実行時切替 |
| **検証ステップ** | `/speckit.analyze`（成果物横断分析） + コンスティチューションゲート | 各ステージの Mob Construction + audit.md | `/gsd-verify-work`（手動受け入れ + 自動診断 + 修正計画） |
| **オープン化形態** | リポジトリ＋ドキュメントサイト＋ CLI パッケージ | リポジトリ＋ Method Definition Paper（CLI は配らない） | npm パッケージ＋ SDK (`@opengsd/gsd-sdk`) |
| **ライセンス** | MIT | **MIT-0** | MIT |
| **ガバナンス** | GitHub 公式 | AWS Labs | コミュニティ (open-gsd team)。Redux 移行の経緯あり |
| **対象規模（自己定義）** | 個人〜大規模 | 大組織（Mob 前提） | ソロビルダー＆小規模チーム |

## 切り口別の解像度

### 「仕様 → コード」の橋渡しをどう作るか

| メソドロジー | アプローチ |
|---|---|
| Spec Kit | **テンプレートを LLM のプロンプト制約**として使う。`[NEEDS CLARIFICATION]` マーカー強制、ゲート式チェックリスト、`implementation-details/` への詳細追い出しなど 7 つの構造化制約 ([詳細](../../frameworks/github-spec-kit.md#テンプレートが-llm-をどう制約するか)) |
| AI-DLC | **明確化質問を多肢選択 + Other 形式のファイル** (`requirement-verification-questions.md`) でやり取り。AI 主導の質問→人間の検証→AI 計画洗練のループ |
| GSD | **Discuss フェーズ**を Spec/Plan の間に独立化。「ロードマップ 1 文では足りない、グレー領域をフェーズ単位で詰める」 |

### 過剰設計 (over-engineering) をどう抑えるか

| メソドロジー | 抑制機構 |
|---|---|
| Spec Kit | コンスティチューション第 VII 条「単純性ゲート」(プロジェクト数 ≤3、将来対応禁止) と第 VIII 条「アンチ抽象化」(フレームワーク直接使用)。違反時は "Complexity Tracking" に正当化を書かないと進めない |
| AI-DLC | 原則 10「No Hard-Wired, Opinionated SDLC Workflows」。**ステージ自体を動的にスキップ**することで、不要な設計フェーズを発動させない |
| GSD | 並列波実行 + アトミックコミットによる「やり直しコストの低減」。過剰設計を**防ぐ**より、捨てやすくする方向 |

### Human-in-the-Loop の入れ方

| メソドロジー | 人間の介入ポイント |
|---|---|
| Spec Kit | `/speckit.clarify` の質問応答、コンスティチューションゲートのレビュー、`/speckit.implement` 後のブラウザ動作確認 |
| AI-DLC | **全ステージで Mob Elaboration / Mob Construction を強制**。承認なしには次に進めない。`audit.md` で監査トレイル |
| GSD | `/gsd-discuss-phase` でビジョン捕捉、`/gsd-verify-work` で受け入れテスト、`mode: interactive` で各ステップ確認（`yolo` で省略可） |

## 使い分けの目安

ここまでの比較から導ける選択基準。**取得時点 (2026-05-28) の理解**で、実プロジェクト適用が増えれば見直す。

### 単一選択で選ぶなら

| ユーザー像 / 制約 | 第一候補 | 理由 |
|---|---|---|
| 仕様の品質と一貫性に強い関心、CLI 主体 | **Spec Kit** | テンプレートの LLM 制約が最も体系化されている |
| 大組織でチーム協業を前提、AWS エコシステム、規制対応 | **AI-DLC** | Mob 様式と監査トレイルが中心機構 |
| ソロ〜小規模、Claude Code 中心、並列実行で速度最重視 | **GSD** | 並列波と context rot 対策が第一級機能 |
| AI コーディングエージェント連携の幅 | **Spec Kit** (30+) or **GSD** (15) | AI-DLC は 7 系列のみ |
| 規制業界（仕様トレーサビリティを規制対応の証跡にしたい） | **Spec Kit** + 自前 Preset、または **AI-DLC** + Extension | どちらも Rule/Verification ペアでブロッキング検証可能 |
| 既存のメソドロジーに後付けで AI を入れる | **AI-DLC** | スキャフォールドが既存ルール機構に被さる形 |

### 複数組み合わせも可能

3 者は直交した切り口（仕様 / 協業 / コンテキスト）なので、原理的には共存可能。例えば:

- **Spec Kit + GSD**: Spec Kit でテンプレート駆動の仕様作成 → GSD の並列波で実装。`.specify/` と `.planning/` が共存する形
- **AI-DLC + GSD の文脈管理**: Mob 様式の協業を保ちつつ、サブエージェントは fresh context で動かす考え方を借りる

実例は確認できていない。実プロジェクトで試した知見は [`playbooks/software-development/`](../../playbooks/software-development/) に追加していく。

## 典型的なアンチパターン（横断）

3 つのメソドロジーで共通して指摘されるか、自分が試して観察した落とし穴:

- **「仕様」フェーズに技術スタックを書く** — Spec Kit の WHAT/WHY ルール、AI-DLC の Inception → Construction 分離、GSD の Discuss → Plan 分離、すべてが同じ境界を引いている
- **明確化を飛ばして計画に進む** — Spec Kit の `[NEEDS CLARIFICATION]`、AI-DLC の Mob Elaboration、GSD の Discuss が同じく「曖昧性の事前可視化」を要求
- **AI が "over-eager" になる** — Spec Kit README が明記。AI-DLC は信条「人間が承認するまで進めない」で抑制。GSD は yolo モードを意図的に切ることで対処
- **永続成果物を `.gitignore` に入れる** — `.specify/`、`aidlc-docs/`、`.planning/` のいずれも**コミット対象**。セッション継続と監査トレイルの両方を破壊する
- **「動いた = 完成」と判定** — 3 メソドロジーとも「Verify / Mob Construction / `/gsd-verify-work`」を別フェーズに切り出して、コード完成と機能完成を区別している

## 共通する弱点 / オープンな問い

3 メソドロジーが**まだ十分に答えていない**と思われる領域:

- **既存大規模リポへの後付け導入** — 全メソドロジーが「ブラウンフィールド対応」を主張するが、実例が乏しい。Spec Kit の N→N+1 適用、AI-DLC の Reverse Engineering、GSD の `/gsd-map-codebase` をそれぞれ実プロジェクトで検証する必要
- **マルチチームでの仕様分割** — 1 リポ内で複数フィーチャー並走するときの仕様ディレクトリ統治はどれも明確でない
- **3 者を組み合わせたときのファイル空間の衝突** — `.specify/` `aidlc-docs/` `.planning/` のいずれかは整理機構を借用するのが現実的かもしれない
- **「コンテキストエンジニアリング」の体系** — Spec Kit 発表ブログが言及している「context engineering との組み合わせ」は別記事予告のまま。GSD はそれに最も近いが体系化されていない

## 関連

### 一次情報

- Spec Kit: [`sources/github/spec-kit/`](../../sources/github/spec-kit/)
- AI-DLC: [`sources/aws/ai-dlc/`](../../sources/aws/ai-dlc/)
- GSD: [`sources/open-gsd/get-shit-done-redux/`](../../sources/open-gsd/get-shit-done-redux/)

### 各メソドロジーの詳細ノート（frameworks/）

- [`frameworks/github-spec-kit.md`](../../frameworks/github-spec-kit.md) — Spec Kit の 4 フェーズ・コンスティチューション・Extensions/Presets
- [`frameworks/aws-ai-dlc.md`](../../frameworks/aws-ai-dlc.md) — AI-DLC の 3 フェーズ・Mob 様式・Workflow Scaffolds
- [`frameworks/open-gsd-get-shit-done-redux.md`](../../frameworks/open-gsd-get-shit-done-redux.md) — GSD の 6 コマンドループ・並列波・`.planning/`

### 隣接トピック

- [`ai-native-startup-lifecycle.md`](ai-native-startup-lifecycle.md) — Anthropic 視点の 4 段階モデル（Idea/MVP/Launch/Scale）。SDLC 全体ではなく事業ステージとの対応
- [`frameworks/anthropic-claude-code.md`](../../frameworks/anthropic-claude-code.md) — Claude Code は 3 メソドロジーすべての対応エージェント

## 拡張余地

- **AI-DLC の Method Definition Paper を取り込んだ後**、信条 5 つを 9 原則に書き換える（取得時点では「原則 10」だけが明示されている）
- **実プロジェクト適用後のレビュー** — `playbooks/software-development/` に各メソドロジーの導入手順が増えたら、ここの比較表に「導入摩擦」「実測パフォーマンス」列を足す
- **OpenSpec / Taskmaster / SDLM** など、GSD README が言及している周辺メソドロジーが台頭したら比較表を拡張
- **コンテキストエンジニアリング** が独立トピックに育ったら、本ノートからの相互リンク先として `topics/cross/context-engineering.md` を起こす
