---
title: "AI-Driven Development Life Cycle (AI-DLC) の適応型ワークフローをオープンソース化"
title_original: "Open-Sourcing Adaptive Workflows for AI-Driven Development Life Cycle (AI-DLC)"
source_url: https://aws.amazon.com/blogs/devops/open-sourcing-adaptive-workflows-for-ai-driven-development-life-cycle-ai-dlc/
captured_at: 2026-05-28
published_at: 2025-11-29
author: Will Matos, Raj Jain, Siddhesh Jog, Raja SP (AWS)
original_language: en
tags: [aws, ai-dlc, open-source, amazon-q-rules, kiro-steering, workflow-scaffolds]
---

> 取り込みメモ: AWS DevOps & Developer Productivity Blog の AI-DLC オープンソース化発表記事の日本語訳。WebFetch で取得した Markdown を翻訳。

# AI-Driven Development Life Cycle (AI-DLC) の適応型ワークフローをオープンソース化

**著者:** Will Matos, Raj Jain, Siddhesh Jog, Raja SP
**公開日:** 2025 年 11 月 29 日
**カテゴリ:** Amazon Q, Amazon Q Developer, Artificial Intelligence, Developer, Developer Tools, Software

---

## 概要

[AI-Driven Development Life Cycle (AI-DLC)](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) は、人間の意思決定権限を維持しつつ、ソフトウェア開発ワークフローに人工知能を統合するアプローチである。このメソドロジーは、開発プロセスにおいて速度と品質の両方を提供することを目指す。

## 3 つの主要な課題

組織がエンジニアリングワークフローに AI を実装する際、繰り返し直面する障害がある:

1. **画一的なワークフロー** — スコープにかかわらず、あらゆるプロジェクトを同一の順序に強制する硬直したプロセス
2. **柔軟な深さの欠如** — ワークフロー各段階の適応性が欠け、過剰設計か厳密さ不足のどちらかに陥る
3. **過剰自動化ツール** — 人間の検証・監督責任を最小化してしまうシステム

## AI-DLC はこれらの課題にどう対処するか

### 課題 1: 「画一的」ワークフローの問題

異なるプロジェクトは異なる経路を要求する:

- 単純な不具合修正には精緻な要件分析は不要
- 純粋なインフラ移植プロジェクトには、ドメインモデリングを伴うアプリケーション設計は不要
- 新機能はセキュリティパッチとは異なるステップを要求する

**AI-DLC の応答:** 原則 10「**No Hard-Wired, Opinionated SDLC Workflows（ハードワイヤされた、強い意見を持つ SDLC ワークフローは持たない）**」を通じて、本手法は「与えられた経路意図に基づき、AI が Level 1 プランを推薦する」ことを許し、硬直したワークフローを規定しない。

### 課題 2: 各段階内での柔軟な深さの欠如

真の適応性はワークフローの「広さ」を超えて、「深さ」と「強度」に及ぶ。軽量のユーティリティ関数を作るのに、フルスケールのドメイン駆動設計や詳細なアーキテクチャモデリングは不要。

**AI-DLC の応答:** 本手法は、複雑さと文脈に合わせて「広さ（段階の選択）」と「深さ（段階の強度）」の両方を適応させる。人間は AI が提案するアプローチを検証・調整し、速度とエンジニアリング規律のバランスを取る。

### 課題 3: 人間の監督を減らすツール

過剰な自動化は「**プロセス萎縮 (process atrophy)**」を生み、開発者が受動的実行へと流れ、内省と監督能力を失う。

**AI-DLC の応答:** フレームワークは全段階で協業的な human-in-the-loop サイクルを要求する:

- **Mob Elaboration（モブ精緻化）** — ステークホルダーが集まり、AI が生成した計画をレビュー・検証する
- **Mob Construction（モブ建設）** — 実行後、チームが最終成果物を検証する
- すべての人間の行動と承認を記録する完全な監査トレイル

## AI-DLC ワークフローサイクル

協業プロセスは以下のパターンに従う:

1. 人間がタスク記述を提供
2. AI が計画を作り、明確化を求める
3. 人間が明確化を提供
4. AI が計画を洗練
5. 人間が計画を承認
6. AI が計画を実行
7. 人間が結果を検証

## 原則から実践へ: ワークフロー・スキャフォールド

手動のプロンプトエンジニアリングではなく、解決策は「**ワークフロー・スキャフォールド (workflow scaffolds)**」 ― AI コーディングエージェントのための Rules またはステアリング (Steering) カスタマイズで、ツール内に AI-DLC 原則を運用化するもの ― を伴う。

このアプローチの主要な成果:

1. **適応的意思決定** — ワークフローが問題の形に合わせ、段階を賢くスキップしたり深めたりする
2. **透明なチェックポイント** — すべての判断ゲートに人間の承認が埋め込まれる
3. **エンドツーエンドの追跡可能性** — すべての成果物・判断・会話が説明責任のためにログされる

## 実装とオープンソースリリース

AWS は AI-DLC ワークフローを [Amazon Q Rules と Kiro Steering Files として](https://github.com/awslabs/aidlc-workflows) オープンソース化し、組織が以下を可能にする:

- 実プロジェクトでステアリングルールを適用する
- プロジェクトスコープへのプロセス適応を観察する
- GitHub を通じてフィードバックを共有し改善に貢献する

「[Amazon Q Developer で AI-DLC を使ってビルドする手順](https://aws.amazon.com/blogs/devops/building-with-ai-dlc-using-amazon-q-developer/)」を提供する補助リソースもある。

## 結論

AI-DLC は、硬直したワークフロー、柔軟性のない深さ、人間の監督を減らすツールに対処するフレームワークを提供する。ワークフロー・スキャフォールドとオープンソースツールを通じて、組織は「**エンジニアリング規律と人間の判断を保ちつつ提供を加速する**」適応的開発を体験できる。

---

## 著者について

**Raja SP** — AWS の Principal Solutions Architect。Developer Transformation Programs をリードし、AI-DLC メソドロジーの創出者。

**Raj Jain** — Senior Solutions Architect, Developer Specialist。元 Amazon Senior Software Development Engineer。出版実績と 12 件の特許を持つ。

**Siddhesh Jog** — AWS Senior Solutions Architect。顧客の AI-DLC への移行を支援することに注力。

**Will Matos** — Principal Specialist Solutions Architect。27 年の技術と AI 経験を持ち、生成 AI による開発者生産性に注力。
