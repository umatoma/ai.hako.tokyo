---
title: "awslabs/aidlc-workflows README (AI-DLC 公式リポジトリ)"
title_original: "AI-DLC (AI-Driven Development Life Cycle)"
source_url: https://github.com/awslabs/aidlc-workflows
captured_at: 2026-05-28
published_at: 2025-11-29
author: AWS Labs (awslabs/aidlc-workflows メンテナー)
original_language: en
tags: [aws, ai-dlc, github, readme, amazon-q, kiro, cursor, claude-code, copilot, codex, cline, license-mit-0]
---

> 取り込みメモ: AWS Labs の AI-DLC ワークフロー公式リポジトリ README の日本語訳。WebFetch で取得した Markdown を翻訳。コードブロック・コマンド・パス・拡張子は原文のまま残す。最新リリースは v0.1.8 (2026-04-20 取得時点)。

# AI-DLC (AI-Driven Development Life Cycle)

プロジェクトのニーズに適応し、品質基準を保ち、ユーザーが統制権を握る、インテリジェントなソフトウェア開発ワークフロー。メソドロジーの詳細は [AWS DevOps Blog](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) と [Method Definition Paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) を参照。

---

## 目次

- Common（共通セットアップ）
- Platform-Specific Setup（プラットフォーム別セットアップ）
- Usage（使い方）
- Three-Phase Adaptive Workflow（3 フェーズ適応型ワークフロー）
- Key Features（主要特徴）
- Extensions（拡張）
- Supporting Tools（補助ツール）
- Tenets（信条）
- Prerequisites（前提条件）
- Troubleshooting（トラブルシュート）
- Version Control Recommendations（バージョン管理の推奨）
- Additional Resources（追加リソース）
- Contributing（貢献）
- License（ライセンス）

---

## 共通セットアップ

1. [Releases ページ](/awslabs/aidlc-workflows/releases/latest) から最新リリース zip `ai-dlc-rules-v<release-number>.zip` をダウンロード
2. プロジェクト外のフォルダ（例: `~/Downloads`）に展開
3. 展開された `aidlc-rules/` には以下が含まれる:
   - `aws-aidlc-rules/` — コアワークフロールール
   - `aws-aidlc-rule-details/` — 条件付き参照される詳細ルール

---

## プラットフォーム別セットアップ

### Kiro

[Kiro Steering Files](https://kiro.dev/docs/cli/steering/) を使う。

**macOS/Linux:**
```bash
mkdir -p .kiro/steering
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rules .kiro/steering/
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details .kiro/
```

**Windows (PowerShell):**
```powershell
New-Item -ItemType Directory -Force -Path ".kiro\steering"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules" ".kiro\steering\"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details" ".kiro\"
```

**Windows (CMD):**
```cmd
mkdir .kiro\steering
xcopy %USERPROFILE%\Downloads\aidlc-rules\aws-aidlc-rules .kiro\steering\aws-aidlc-rules\ /E /I
xcopy %USERPROFILE%\Downloads\aidlc-rules\aws-aidlc-rule-details .kiro\aws-aidlc-rule-details\ /E /I
```

**プロジェクト構造:**
```
<project-root>/
├── .kiro/
│   ├── steering/
│   │   ├── aws-aidlc-rules/
│   ├── aws-aidlc-rule-details/
```

**検証:**

- Kiro IDE: ステアリングファイルパネルで `core-workflow` エントリを確認
- Kiro CLI: `kiro-cli` を実行後、`/context show` を実行

---

### Amazon Q Developer IDE プラグイン / 拡張

[Amazon Q Rules](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/context-project-rules.html) を使う。

**macOS/Linux:**
```bash
mkdir -p .amazonq/rules
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rules .amazonq/rules/
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details .amazonq/
```

**Windows (PowerShell):**
```powershell
New-Item -ItemType Directory -Force -Path ".amazonq\rules"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules" ".amazonq\rules\"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details" ".amazonq\"
```

**Windows (CMD):**
```cmd
mkdir .amazonq\rules
xcopy %USERPROFILE%\Downloads\aidlc-rules\aws-aidlc-rules .amazonq\rules\aws-aidlc-rules\ /E /I
xcopy %USERPROFILE%\Downloads\aidlc-rules\aws-aidlc-rule-details .amazonq\aws-aidlc-rule-details\ /E /I
```

**プロジェクト構造:**
```
<project-root>/
├── .amazonq/
│   ├── rules/
│   │   ├── aws-aidlc-rules/
│   ├── aws-aidlc-rule-details/
```

**検証:** Amazon Q Chat を開き、`Rules` ボタンをクリックし、`.amazonq/rules/aws-aidlc-rules` のエントリを確認。

---

### Cursor IDE

[Cursor Rules](https://cursor.com/docs/context/rules) を使う。

**Option 1: Project Rules（推奨）**

**Unix/Linux/macOS:**
```bash
mkdir -p .cursor/rules

cat > .cursor/rules/ai-dlc-workflow.mdc << 'EOF'
---
description: "AI-DLC (AI-Driven Development Life Cycle) adaptive workflow for software development"
alwaysApply: true
---
EOF
cat ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md >> .cursor/rules/ai-dlc-workflow.mdc

mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Option 2: AGENTS.md（シンプルな代替）**

**Unix/Linux/macOS:**
```bash
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md ./AGENTS.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**検証:** Cursor Settings → Rules, Commands を開き、Project Rules の下に `ai-dlc-workflow` があることを確認。

**Option 1 のディレクトリ構造:**
```
<my-project>/
├── .cursor/
│   └── rules/
│       └── ai-dlc-workflow.mdc
└── .aidlc-rule-details/
    ├── common/
    ├── inception/
    ├── construction/
    ├── extensions/
    └── operations/
```

---

### Cline

Cline Rules を使ってインテリジェントワークフローを実装する。

**Option 1: .clinerules ディレクトリ（推奨）**

**Unix/Linux/macOS:**
```bash
mkdir -p .clinerules
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md .clinerules/
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Option 2: AGENTS.md（代替）**

**Unix/Linux/macOS:**
```bash
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md ./AGENTS.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**検証:** チャット入力下の Rules ポップオーバーを確認し、`core-workflow.md` がリスト・アクティブであることを検証。

---

### Claude Code

Claude Code のプロジェクトメモリファイル (`CLAUDE.md`) を使う。

**Option 1: プロジェクトルート（推奨）**

**Unix/Linux/macOS:**
```bash
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md ./CLAUDE.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Option 2: .claude ディレクトリ**

**Unix/Linux/macOS:**
```bash
mkdir -p .claude
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md .claude/CLAUDE.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**検証:**

- プロジェクトディレクトリで Claude Code を起動
- `/config` コマンドで設定を表示
- 「このプロジェクトで現在アクティブな指示は何ですか？」と質問

---

### GitHub Copilot

[GitHub Copilot custom instructions](https://code.visualstudio.com/docs/copilot/customization/custom-instructions) を使う ― 自動検出・適用される。

**Unix/Linux/macOS:**
```bash
mkdir -p .github
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md .github/copilot-instructions.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**検証:**

- VS Code を開く
- Copilot Chat (Cmd/Ctrl+Shift+I) を開く
- **Configure Chat**（歯車アイコン）> **Chat Instructions** を選択
- `copilot-instructions` がリストされていることを確認
- またはチャットで `/instructions` をタイプ

---

### OpenAI Codex

[Codex AGENTS.md 規約](https://developers.openai.com/codex/guides/agents-md) を使う ― 自動検出・ロードされる。

**Unix/Linux/macOS:**
```bash
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md ./AGENTS.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**検証:** Codex セッションを開始し、「Using AIDLC analyze the project?」または「Using AIDLC what workflow do you see?」と質問。

**設定メモ:** `AGENTS.md` ファイルは Codex の指示予算 (instruction budget) に収まるよう設計されている。プロジェクトドキュメントが上限を超える場合、`config.toml` の `project_doc_max_bytes` を調整:

```toml
project_doc_max_bytes = 65536  # 例
```

---

### その他のエージェント

AI-DLC は、プロジェクトレベルのルールをサポートする任意のコーディングエージェントで動作する。一般的なアプローチ:

1. `aws-aidlc-rules/` をエージェントがプロジェクトルールを読む場所に置く
2. `aws-aidlc-rule-details/` を兄弟階層に置く（ルール参照のため）

エージェントにルール規約がない場合は、両フォルダをプロジェクトルートに置き、エージェントに `aws-aidlc-rules/` をルールディレクトリとして指し示す。

---

## 使い方

1. チャットで **「Using AI-DLC, ...」** のフレーズで意図を述べてプロジェクトを開始
2. AI-DLC ワークフローが自動的に有効化され、開発を導く
3. AI-DLC が提示する構造化された質問に答える
4. 生成されたあらゆる計画を注意深くレビューし、監督的検証を提供する
5. どのステージが実行されるかを確認するために実行計画をレビュー
6. 各ステージで成果物をレビューし承認することで統制を保つ
7. すべての成果物は `aidlc-docs/` ディレクトリに生成される

---

## 3 フェーズ適応型ワークフロー

### 🔵 INCEPTION フェーズ

**WHAT（何を）** と **WHY（なぜ）** を決定する。

- 要件分析と検証
- ユーザーストーリー作成（該当時）
- アプリケーション設計と並行開発用ユニットの作成
- リスク評価と複雑さ評価

### 🟢 CONSTRUCTION フェーズ

**HOW（どう）** 作るかを決定する。

- 詳細コンポーネント設計
- コード生成と実装
- ビルド設定とテスト戦略
- 品質保証と検証

### 🟡 OPERATIONS フェーズ

デプロイと監視（将来）。

- デプロイ自動化とインフラ
- 監視と可観測性のセットアップ
- 本番運用準備の検証

---

## 主要特徴

| 特徴 | 説明 |
|---|---|
| **適応的インテリジェンス** | 特定のリクエストに価値を加えるステージのみを実行 |
| **コンテキスト認識** | 既存コードベースと複雑さ要件を分析 |
| **リスクベース** | 複雑な変更は包括的扱い、シンプルな変更は効率的に保つ |
| **質問駆動** | チャットではなくファイル内で構造化された多肢選択質問 |
| **常に統制下** | 実行計画をレビューし各フェーズを承認 |
| **拡張可能** | カスタムルール（セキュリティ、コンプライアンス、組織固有）をコアに重ねられる |

---

## 拡張 (Extensions)

AI-DLC は、コアワークフローに追加ルールを重ねる拡張システムをサポートする。拡張は `aws-aidlc-rule-details/extensions/` 配下のマークダウンファイルで、カテゴリ（例: `security/`, `testing/`）でグループ化される。

### 拡張の仕組み

各拡張は同じディレクトリの 2 ファイルから成る:

- **ルールファイル**（例: `security-baseline.md`） — 拡張のルール
- **Opt-in ファイル**（例: `security-baseline.opt-in.md`） — 構造化された多肢選択質問

ワークフロー開始時、AI-DLC は `extensions/` ディレクトリをスキャンし、`*.opt-in.md` ファイルをロードする。Requirements Analysis 中、各 opt-in プロンプトを提示する。ユーザーが opt-in すれば、対応するルールファイル（命名から導出: `.opt-in.md` を剥がして `.md` を付ける）がロードされる。opt-out なら、ルールファイルはロードされない。`*.opt-in.md` が一致しない拡張は常に強制される。

有効化されると、拡張ルールは**ブロッキング制約 (blocking constraints)** となる ― 各ステージでモデルは進む前にコンプライアンスを検証する。

### 組み込み拡張

```
aws-aidlc-rule-details/
└── extensions/
    ├── security/                      # 拡張カテゴリ
    │   └── baseline/
    │       ├── security-baseline.md          # ベースラインセキュリティルール
    │       └── security-baseline.opt-in.md   # opt-in プロンプト
    └── testing/                       # 拡張カテゴリ
        └── property-based/
            ├── property-based-testing.md          # プロパティベーステストルール
            └── property-based-testing.opt-in.md   # opt-in プロンプト
```

> **重要:** セキュリティ拡張ルールは、AI-DLC ワークフローで効果的なセキュリティルールを構築するための方向性参照である。各組織は本番ワークフローで展開する前に、自社のセキュリティルールを構築・カスタマイズ・徹底テストすべき。

### 独自拡張の追加

1. `extensions/` 配下にディレクトリを作る（例: `security/compliance/` や `performance/baseline/`）
2. **ルールファイル**（例: `compliance.md`）を追加。`security-baseline.md` の構造に従う:
   - 各ルールを見出しで定義: `## Rule <PREFIX-NN>: <Title>`。PREFIX は短いカテゴリ識別子、NN は通し番号（例: `COMPLIANCE-01`, `COMPLIANCE-02`）。ID は監査ログとコンプライアンスサマリーで参照されるため、ロードされたすべての拡張で一意でなければならない。
   - **Rule** セクションで要件を記述
   - **Verification** セクションでモデルが評価すべき具体的チェックを含める
3. 命名規約 `<name>.opt-in.md`（例: `compliance.opt-in.md`）でマッチする **opt-in ファイル**を追加。期待される形式は `security-baseline.opt-in.md` を参照。このファイルを省略すると拡張は常に強制される（ユーザー opt-out なし）。
4. ルールはデフォルトでブロッキング ― 検証基準を満たさない場合、検出が解決されるまでステージは進めない。

---

## 補助ツール

`scripts/` ディレクトリには AI-DLC ワークフローを強化する補助ツールがある。

### AIDLC Evaluator

**場所:** [`scripts/aidlc-evaluator/`](https://github.com/awslabs/aidlc-workflows/blob/main/scripts/aidlc-evaluator)

AI-DLC ワークフローへの変更を検証する自動化テストとレポートフレームワーク。提供:

- **Golden Test Cases** — 検証用のベースラインテストケース
- **Execution Framework** — 評価パイプラインを通じたテストケース実行のオーケストレーション
- **Semantic Evaluation** — 出力の正しさと完全性を AI ベースで評価
- **Code Evaluation** — 静的解析（リント、セキュリティスキャン、重複検出）
- **NFR Evaluation** — 非機能要件テスト（トークン使用量、実行時間、モデル間一貫性）
- **CI/CD Integration** — PR 検証の自動パイプライン

**クイックスタート:**
```bash
cd scripts/aidlc-evaluator
uv sync
uv run python run.py test
```

**ドキュメント:** [scripts/aidlc-evaluator/README.md](https://github.com/awslabs/aidlc-workflows/blob/main/scripts/aidlc-evaluator/README.md)

---

### AIDLC Design Reviewer

**場所:** [`scripts/aidlc-designreview/`](https://github.com/awslabs/aidlc-workflows/blob/main/scripts/aidlc-designreview)

⚠️ **実験的機能** — AWS Bedrock 経由で Claude モデルを使い、AIDLC 設計成果物を解析する AI 駆動の設計レビューツール。

**特徴:**

- **マルチエージェントレビュー** — 3 種の特化 AI エージェント（Critique、Alternatives、Gap Analysis）
- **品質スコア** — 重み付き重大度分析と実行可能な推奨
- **2 つのデプロイメントモード:**
  - **CLI ツール** — CI/CD パイプライン向けのオンデマンドレビュー
  - **Claude Code フック** — 開発中のリアルタイムレビュー（実験的）

**インストール (CLI ツール):**
```bash
cd scripts/aidlc-designreview
uv sync --extra test
source .venv/bin/activate  # Linux/Mac
design-reviewer --aidlc-docs /path/to/aidlc-docs
```

**インストール (Claude Code フック):**
```bash
# ワークスペースルートから
./scripts/aidlc-designreview/tool-install/install-linux.sh      # Linux
./scripts/aidlc-designreview/tool-install/install-mac.sh        # macOS
.\scripts\aidlc-designreview\tool-install\install-windows.ps1   # Windows PowerShell
```

インストーラーはワークスペースルートを自動検出し、フックを `.claude/` にインストール。

**ドキュメント:**

- [scripts/aidlc-designreview/README.md](https://github.com/awslabs/aidlc-workflows/blob/main/scripts/aidlc-designreview/README.md) — メインドキュメント
- [scripts/aidlc-designreview/INSTALLATION.md](https://github.com/awslabs/aidlc-workflows/blob/main/scripts/aidlc-designreview/INSTALLATION.md) — フックインストールガイド

---

## 信条 (Tenets)

意思決定を導くコア原則:

- **重複なし (No duplication)** — 真実の源は一箇所に。新ツール・新形式のサポートに特定ファイルが必要な場合、別コピーを保守するのではなく source から生成する。

- **メソドロジーファースト (Methodology first)** — AI-DLC は本質的にメソドロジーであり、ツールではない。利用者は何かをインストールせずに始められるべき。将来採用や拡張を助ける場合に限り、便利ツール（スクリプト、CLI）も検討。

- **再現可能 (Reproducible)** — ルールは、異なるモデルでも類似の結果を生むほど明確であるべき。モデルの挙動は異なるが、メソドロジーは明示的なガイダンスで分散を最小化すべき。

- **非依存 (Agnostic)** — メソドロジーは任意の IDE、エージェント、モデルで動く。特定ツールやベンダーに縛られない。

- **Human in the loop（人間が輪の中に）** — 重要判断には明示的なユーザー確認が必要。エージェントが提案し、人間が承認する。

---

## 前提条件

サポートされる Assisted AI Coding のプラットフォーム/ツールのいずれかをインストール:

| プラットフォーム | インストールリンク |
|---|---|
| Kiro | [Install](https://kiro.dev/) |
| Kiro CLI | [Install](https://kiro.dev/cli/) |
| Amazon Q Developer IDE Plugin | [Install](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html) |
| Cursor IDE | [Install](https://cursor.com/) |
| Cline VS Code Extension | [Install](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) |
| Claude Code CLI | [Install](https://github.com/anthropics/claude-code) |
| GitHub Copilot | [Install](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) + [Chat](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) |

---

## トラブルシュート

### 一般的な問題

| 問題 | 解決策 |
|---|---|
| ルールがロードされない | プラットフォームの正しい場所にファイルが存在するか確認 |
| ファイルエンコーディングの問題 | ファイルが UTF-8 エンコードか確認 |
| セッションでルールが適用されない | ファイル変更後に新しいチャットセッションを開始 |
| ルール詳細がロードされない | `.aidlc-rule-details/` がサブディレクトリ込みで存在するか確認 |

### プラットフォーム別の問題

#### Amazon Q Developer / Kiro

- `/context show` でルールロードを検証
- `.amazonq/rules/` または `.kiro/steering/` のディレクトリ構造を確認

#### Cursor

- "Apply Intelligently" を使う場合、frontmatter に description を定義
- **Cursor Settings → Rules** でルール有効化を確認
- ルールが 500 行を超える場合は、複数の焦点を絞ったルールに分割

#### Cline

- チャット入力下の Rules ポップオーバーを確認
- ポップオーバー UI でルールファイルのオン/オフ切替

#### Claude Code

- `/config` コマンドで現在の設定を表示
- 「このプロジェクトで現在アクティブな指示は何ですか？」と質問

#### GitHub Copilot

- **Configure Chat**（歯車）> **Chat Instructions** を選択しロードを検証
- チャット入力で `/instructions` をタイプしてアクティブな指示ファイルを表示
- ワークスペースルートに `.github/copilot-instructions.md` が存在することを確認

### Windows のファイルパス問題

- マークダウンファイル内のファイルパスではフォワードスラッシュ `/` を使う
- バックスラッシュの Windows パスは正しく動作しないことがある

---

## バージョン管理の推奨

**リポジトリにコミット:**
```
CLAUDE.md
AGENTS.md
.amazonq/rules/
.amazonq/aws-aidlc-rule-details/
.kiro/steering/
.kiro/aws-aidlc-rule-details/
.cursor/rules/
.clinerules/
.github/copilot-instructions.md
.aidlc-rule-details/
```

**任意 — `.gitignore` に追加:**
```
# Local-only settings
.claude/settings.local.json
```

---

## 生成される aidlc-docs/ リファレンス

AI-DLC ワークフローが生成するすべてのドキュメント成果物の完全なリファレンス: [docs/GENERATED_DOCS_REFERENCE.md](https://github.com/awslabs/aidlc-workflows/blob/main/docs/GENERATED_DOCS_REFERENCE.md)

---

## 追加リソース

| リソース | リンク |
|---|---|
| AI-DLC Method Definition Paper | [Paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) |
| AI-DLC Methodology Blog | [AWS Blog](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) |
| AI-DLC Open-source Launch Blog | [AWS Blog](https://aws.amazon.com/blogs/devops/open-sourcing-adaptive-workflows-for-ai-driven-development-life-cycle-ai-dlc/) |
| AI-DLC Example Walkthrough Blog | [AWS Blog](https://aws.amazon.com/blogs/devops/building-with-ai-dlc-using-amazon-q-developer/) |
| Amazon Q Developer Documentation | [Docs](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html) |
| Kiro CLI Documentation | [Docs](https://kiro.dev/docs/cli/steering/) |
| Cursor Rules Documentation | [Docs](https://cursor.com/docs/context/rules) |
| Claude Code Documentation | [GitHub](https://github.com/anthropics/claude-code) |
| GitHub Copilot Documentation | [Docs](https://docs.github.com/en/copilot) |
| Working with AI-DLC (対話パターンとコツ) | [docs/WORKING-WITH-AIDLC.md](https://github.com/awslabs/aidlc-workflows/blob/main/docs/WORKING-WITH-AIDLC.md) |
| Contributing Guidelines | [CONTRIBUTING.md](https://github.com/awslabs/aidlc-workflows/blob/main/CONTRIBUTING.md) |
| Code of Conduct | [CODE_OF_CONDUCT.md](https://github.com/awslabs/aidlc-workflows/blob/main/CODE_OF_CONDUCT.md) |

---

## 貢献

詳細は [CONTRIBUTING](https://github.com/awslabs/aidlc-workflows/blob/main/CONTRIBUTING.md#security-issue-notifications) を参照。

---

## ライセンス

このライブラリは **MIT-0 License** の下でライセンスされている。詳細は [LICENSE](https://github.com/awslabs/aidlc-workflows/blob/main/LICENSE) ファイルを参照。

---

## リポジトリメタデータ（取得時点 2026-05-28）

- **リポジトリ:** awslabs/aidlc-workflows
- **最新リリース:** v0.1.8（2026-04-20）
- **スター:** 2.5k
- **フォーク:** 412
- **言語:** Python 83.8%, Shell 9.6%, HTML 4.0%, Jinja 1.1%, PowerShell 1.0%, Mermaid 0.4%, Dockerfile 0.1%
- **ステータス:** Public, Open Source
