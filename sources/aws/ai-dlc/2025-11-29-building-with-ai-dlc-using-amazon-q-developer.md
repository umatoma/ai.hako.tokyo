---
title: "Amazon Q Developer で AI-DLC を使ってビルドする"
title_original: "Building with AI-DLC using Amazon Q Developer"
source_url: https://aws.amazon.com/blogs/devops/building-with-ai-dlc-using-amazon-q-developer/
captured_at: 2026-05-28
published_at: 2025-11-29
author: Will Matos, Raj Jain, Siddhesh Jog, Raja SP (AWS)
original_language: en
tags: [aws, ai-dlc, amazon-q-developer, walkthrough, tutorial, river-crossing-puzzle]
---

> 取り込みメモ: AWS DevOps & Developer Productivity Blog の AI-DLC 実装ウォークスルー記事の日本語訳。WebFetch で取得した Markdown を翻訳。コードブロック・コマンドは原文のまま残す。

# Amazon Q Developer で AI-DLC を使ってビルドする

**著者:** Will Matos, Raj Jain, Siddhesh Jog, Raja SP
**公開日:** 2025 年 11 月 29 日
**カテゴリ:** Amazon Machine Learning, Amazon Q, Amazon Q Developer, Artificial Intelligence, Best Practices, Developer Tools, Software

---

## AI-DLC ワークフロー概要

AI-Driven Development Life Cycle (AI-DLC) メソドロジーは、ソフトウェア開発における大きな転換を表す ― 定型タスクを戦略的に AI へ委任しつつ、重要判断には人間の監督を維持する。

ワークフローは 3 つの主要フェーズから成る:

1. **Inception** — 計画とアーキテクチャ
2. **Construction** — 設計と実装
3. **Operations** — デプロイと監視

各フェーズには特定のソフトウェア開発ライフサイクル機能に対応する明確なステージが含まれる。ワークフローはリクエスト・コードベース・複雑さを分析することで、プロジェクト要件に合わせて必要なステージを決定する。単純なバグ修正は直接コード生成に進み、複雑な機能は要件分析・アーキテクチャ設計・詳細テストを要求する。

メソドロジーは、構造化されたマイルストーンと透明な意思決定を通じて品質と統制を保つ。「各フェーズで AI-DLC は明確化質問を投げ、実行計画を作り、承認を待つ。」

---

## 前提条件

開始前に必要なもの:

- 認証用の AWS アカウントまたは AWS Builder ID
- Amazon Q Developer でサポートされる統合開発環境 (IDE)
- Amazon Q Developer 拡張機能のインストール
- AWS クラウドバックエンドとの認証設定

任意: IDE 内で生成された図を可視化する Mermaid ビュアープラグイン。

---

## はじめに: 川渡りパズルアプリを作る

このウォークスルーでは、AI-DLC メソドロジーを使ってシンプルな川渡りパズル (River Crossing Puzzle) の Web UI アプリを構築する。

### Step 1: GitHub リポジトリをクローン

```
git clone https://github.com/awslabs/aidlc-workflows.git
```

### Step 2: Q Developer ルールをロード

リポジトリの README.md の手順に従い、ルールファイルをプロジェクトフォルダにコピーする。

### Step 3: Amazon Q Developer をインストール・認証

VS Code でプロジェクトフォルダを開き、Amazon Q Chat パネルにアクセスし、AI-DLC ワークフロールールがロードされていることを確認する。

### Step 4: ワークフローを開始

問題文を「Using AI-DLC」で始める:

```
Using AI-DLC let's build a web application to solve the river crossing puzzle.
```

ワークフローは歓迎メッセージと AI-DLC メソドロジーの概要で応答し、Inception フェーズの Workspace Detection から入ることを示す。

---

## Phase 1: Inception

### Workspace Detection（ワークスペース検出）

AI-DLC は現在のワークスペースを分析し、グリーンフィールド（新規）かブラウンフィールド（既存）かを判定する。ワークフローは AI-DLC で生成されるすべての成果物を保存する `aidlc-docs` フォルダの作成許可を求める。

2 つのファイルが作られる:

- **aidlc-state.md** — エラー復旧とセッション継続のための進捗を追跡
- **audit.md** — ユーザープロンプトと応答を追跡可能性のために保存

グリーンフィールドプロジェクトでは、ワークフローは Reverse Engineering（リバースエンジニアリング）ではなく Requirements Analysis（要件分析）に進む。

### Requirements Analysis（要件分析）

「AI-DLC ワークフローは我々の高レベル問題文を Q Developer に提示し、Q Developer は複数の要件明確化質問で応答した。」

Amazon Q は質問を多肢選択式（自由記述の "Other" 付き）で提示する。ワークフローは:

- `requirement-verification-questions.md` を作成
- パズルのバリアント、ユーザー操作方法、データ永続化、リーダーボード機能などについて明確化質問を投げる
- 「Answered」とマークされたユーザー応答を待つ

Amazon Q は応答を処理し、矛盾や曖昧性を特定してから次へ進む。完了時に包括的な `requirements.md` ドキュメントが生成され、以下を含む:

- Intent Analysis Summary（意図分析サマリー）
- User Request の詳細
- Functional Requirements（機能要件）

ユーザーは変更を要求するか、ユーザーストーリーを追加するか、承認して継続するかを選べる。

### Workflow Planning（ワークフロー計画）

要件が確立されると、ワークフローは特定の AI-DLC ステージの実行を計画する。`execution-plan.md` ファイルは以下を示す:

- 実行を推奨するステージ
- 複雑さ分析に基づきスキップするステージ
- リスク評価
- ワークフロー可視化図

ワークフローは、シンプルなアプリでは条件付きステージをスキップし、Construction フェーズの Code Generation Planning に直接進むことを推奨する。

---

## Phase 2: Construction

### Code Generation Planning（コード生成計画）

コードを生成する前に、AI-DLC は詳細な番号付き計画を `{unit-name}-code-generation-plan.md` に作る。計画は:

- 実装を明示的なステップに分解
- ビジネスロジック、API 層、データ層、テスト、ドキュメントをカバー
- 透明性と進捗追跡のためチェックボックスを含む
- 進む前にユーザー変更を許す

パズルアプリでは、提案ワークフローには 8 つのステップが含まれる: HTML 構造、CSS スタイリング、JavaScript ゲームロジック、テスト、ドキュメント。

### Code Generation（コード生成）

Code Generation ステージは承認された計画をステップごとに実行し、ビジネスロジック・API・データ層・テスト・ドキュメントを含むコード成果物を生成する。「完了ステップはチェックボックスでマークされ、進捗が追跡され、ストーリーの追跡可能性が保証された上で、生成されたコードがユーザー承認のために提示される。」

例のプロジェクトでは、要件で指定された通り、埋め込みスタイリングと JavaScript を含む単一の `index.html` ファイルが生成される。

### Build and Test（ビルドとテスト）

Construction フェーズ最後のステージで、包括的な指示ファイルが作成され、以下を文書化する:

- ビルドとパッケージングのガイダンス
- 依存関係とコマンド
- 期待される結果を含むテスト実行ステップ
- ビルド/テスト状況サマリー
- プロジェクトデプロイ準備状態

---

## Phase 3: Operations

Operations フェーズはデプロイと監視をカバーする。この例では AI-DLC ワークフローは Construction フェーズの後で終了する。

---

## アプリのテスト

`index.html` を Web ブラウザで開くと、川渡りパズルアプリが表示される。フレームワークなしで HTML・CSS・JavaScript で構築されたグラフィカル Web UI は期待通りに動作し、ユーザーはパズルを解ける。

---

## AI-DLC メソドロジーの主要特徴

**Human-in-the-Loop:** 「演習は AI-DLC が AI 自動化と人間の監督をどうバランスさせ、品質や統制を犠牲にせず生産性を高めるかを成功裏に示した。」

**適応的ワークフロー:** メソドロジーはプロジェクトの複雑さに応じて厳密さを適応させ、複雑なプロジェクトでは包括的プロセスを、シンプルなアプリでは効率的処理を実装する。

**透明性と追跡可能性:** 「すべての判断・入力・応答が追跡可能性のため監査トレイルにログされる。」

**構造化された監督:** 意思決定は明確なマイルストーンで起こり、重要なチェックポイントでユーザー承認が要求される。

---

## Project Rules 実装

Amazon Q Developer の Project Rules 機能が AI-DLC ワークフローを実装する。設定は以下を使う:

- `.amazonq/rules` フォルダの単一の `aws-aidlc-rules/core-workflow.md` を主要文脈として
- `aws-aidlc-rule-details` フォルダに詳細なフェーズ・ステージレベルのルールを格納し、必要に応じて動的にロード
- 各フェーズ用のサブフォルダと、横断的ルール用の共通フォルダで整理

この構造により、任意時点で必要な情報だけを文脈に保ち、トークン消費を最適化する。

---

## リソース

- [GitHub Repository: aidlc-workflows](https://github.com/awslabs/aidlc-workflows)
- [Amazon Q Developer Documentation](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html)
- [AI-DLC Method Definition Paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/)
- [AI-Native Builders Community](https://ai-nativebuilders.org/)

---

## 著者について

**Raja SP** — AWS の Principal Solutions Architect。Developer Transformation Programs をリード。AI Driven Development Lifecycle メソドロジーの創出者。

**Raj Jain** — AWS の Senior Solutions Architect, Developer Specialist。元 Amazon シニアエンジニアでプラットフォームセキュリティインフラに注力。

**Siddhesh Jog** — AWS の Senior Solutions Architect。顧客の AI 駆動開発プラクティスへの移行支援に情熱を注ぐ。

**Will Matos** — AWS の Next Generation Developer Experience チームの Principal Specialist Solutions Architect。生成 AI と開発者生産性に注力。
