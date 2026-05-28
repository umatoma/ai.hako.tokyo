---
title: "AI-Driven Development Life Cycle: ソフトウェアエンジニアリングの再構想"
title_original: "AI-Driven Development Life Cycle: Reimagining Software Engineering"
source_url: https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/
captured_at: 2026-05-28
published_at: 2025-07-31
author: Raja SP (Principal Solutions Architect, AWS)
original_language: en
tags: [aws, ai-dlc, methodology, amazon-q-developer, kiro, software-development]
---

> 取り込みメモ: AWS DevOps & Developer Productivity Blog の AI-DLC 発表記事の日本語訳。WebFetch で取得した Markdown を翻訳。図表は `[Figure: 内容の概要]` の形で位置と内容だけ残している（再現は原文の図を参照）。

# AI-Driven Development Life Cycle: ソフトウェアエンジニアリングの再構想

**著者:** Raja SP
**公開日:** 2025 年 7 月 31 日
**カテゴリ:** [Amazon Q Developer](https://aws.amazon.com/blogs/devops/category/amazon-q/amazon-q-developer/), [Generative AI](https://aws.amazon.com/blogs/devops/category/artificial-intelligence/generative-ai/)

---

## はじめに

ビジネス・テクノロジーリーダーは、生産性を高め、速度を加速し、実験を奨励し、市場投入時間を短縮し、開発者体験 (developer experience) を改善することを継続的に求めている。これらの目的がソフトウェア開発のイノベーションを駆動しており、ますます人工知能で推進されつつある。[Amazon Q Developer](https://aws.amazon.com/q/developer/) や [Kiro](https://kiro.dev/) のような生成 AI ツールは、ソフトウェア作成を変容させ始めている。組織は現在、AI を 2 つのアプローチで使っている: ドキュメント作成やコード補完といった特定タスクを AI が強化する **AI 支援開発 (AI-assisted development)** と、AI が人間の介入なしにアプリ全体を生成する **AI 自律開発 (AI-autonomous development)** だ。どちらのアプローチも、速度と品質の両面で AI-DLC が対処しようとしている準最適な結果をもたらしてきた。

## なぜソフトウェアにおける AI の変革的アプローチが必要なのか？

既存のソフトウェア開発手法は、プロダクトオーナー、開発者、アーキテクトが計画・会議・その他のソフトウェア開発ライフサイクル儀礼といったコア外の活動に多大な時間を費やす、人間駆動の長時間プロセス向けに設計されている。AI を「アシスタント」として後付けするだけでは、AI の能力を制約しつつ、時代遅れの非効率を強化することになる。AI の力を真に活用し生産性目標を達成するには、組織はソフトウェア開発ライフサイクルへのアプローチ全体を再構想する必要がある。

変革的な結果を達成するには、AI を開発プロセスにおける**中心的協力者・チームメイト**として位置付け、ソフトウェア開発ライフサイクル全体を通じてその能力を活用しなければならない。これが [AI-Driven Development Lifecycle (AI-DLC)](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) ― ソフトウェア開発に AI 能力を完全に統合するために設計された新しいメソドロジー ― の基盤だ。

## AI Driven Development Life Cycle (AI-DLC) とは？

AI-DLC は AI 中心のソフトウェア開発への変革的アプローチで、次の 2 つの強力な次元を強調する:

- **人間の監督を伴う AI 駆動実行 (AI Powered Execution with Human Oversight)**: AI は詳細な作業計画を体系的に作成し、能動的に明確化とガイダンスを求め、重要な判断を人間に委ねる。これは、ビジネス要件についての文脈的理解と知識を持つのは人間だけだから、極めて重要だ。

- **動的なチーム協業 (Dynamic Team Collaboration)**: AI が定型タスクを処理する一方、チームは協業空間に集まり、リアルタイムの問題解決・創造的思考・迅速な意思決定を行う。孤立した作業から高エネルギーのチームワークへの移行が、イノベーションと提供を加速する。

[Figure: AI を中心に、その周りで部門横断のチームメンバーが互いに協業している AI 中心図]

この 2 つの次元によって、品質を妥協することなくソフトウェアをより速く提供できる。

## AI-DLC はどう動くのか？

AI-DLC の本質は、AI がワークフローを開始・指揮する新しいメンタルモデルで動くこと:

[Figure: 「AI が計画を作る → 明確化を求める → 計画を実装する」のサイクルと、その間に人間が重要判断を行うことを示す図]

このパターン ― AI が計画を作り、文脈を得るために明確化質問を投げ、人間の検証を得てから実装する ― は SDLC のあらゆる活動で素早く繰り返され、すべての開発経路に統一的なビジョンとアプローチを提供する。

AI-DLC におけるソフトウェア開発は、わかりやすい 3 つのフェーズで起こる:

- **Inception フェーズ**: AI がビジネス意図を詳細な要件・ストーリー・ユニットに変換する ― 「**Mob Elaboration（モブ精緻化）**」を通じて、チーム全員が能動的に AI の質問と提案を検証する。

- **Construction フェーズ**: Inception フェーズで検証された文脈を使い、AI が論理アーキテクチャ、ドメインモデル、コード解、テストを「**Mob Construction（モブ建設）**」で提案する ― チームが技術判断とアーキテクチャ選択にリアルタイムで明確化を提供する。

- **Operations フェーズ**: AI が前フェーズで蓄積した文脈を適用し、Infrastructure as Code とデプロイを管理する ― チームの監督下で。

各フェーズが次のフェーズにより豊かな文脈を提供し、AI はますます情報に裏付けられた提案を出せるようになる。

[Figure: Inception → Construction → Operation の 3 フェーズ図]

AI は計画・要件・設計成果物をプロジェクトリポジトリに保存することで、すべてのフェーズで永続的な文脈を維持し、複数セッションをまたいだ作業の継続をシームレスに保証する。

[AI-DLC は新しい用語と儀礼を導入し](https://prod.d13rzhkk8cj2z0.amplifyapp.com/)、AI 駆動で高度に協業的なアプローチを反映する。伝統的な「スプリント (sprints)」は「ボルト (bolts)」 ― 週単位ではなく時間や日単位で測られる、より短くより集中した作業サイクル ― に置き換えられる。「エピック (Epics)」は「ユニット・オブ・ワーク (Units of Work)」に置き換えられる。この用語の変更は、本手法が速度と継続的提供を強調していることを示す。同様に、他の馴染みあるアジャイル用語も AI 中心ワークフローに合わせて再考され、メソドロジーの革新的アプローチをよりよく表す語彙を作る。

## このメソドロジーの利点は？

- **速度 (Velocity)**: AI-DLC が提供する最大の利点。AI が要件・ストーリー・設計・コード・テストといった成果物を素早く生成・洗練するため、プロダクトオーナー・アーキテクト・開発者は以前は週単位だったタスクを時間や日単位で完了できる。

- **イノベーション (Innovation)**: AI による加速と重作業の引き受けが、イノベーションのための大幅な時間を解放し、創造的な解の探求と可能性の境界の押し広げを可能にする。

- **品質 (Quality)**: 継続的な明確化により、チームは抽象的な「AI の意図解釈」ではなく、まさに思い描いた通りのものを作る。結果としてプロダクトはビジネス目標とより密接に整合する。AI は組織固有の標準（コーディング慣行、設計パターン、セキュリティ要件）を一貫して適用しつつ、包括的なテストスイートを生成することで品質を高める。このエンドツーエンドの AI 統合が、要件からデプロイまでの整合性と追跡可能性を改善する。

- **市場応答性 (Market Responsiveness)**: AI-DLC の素早い開発サイクルが、市場需要とユーザーフィードバックへの素早い応答を可能にし、要件への適応を加速する。

- **開発者体験 (Developer Experience)**: AI-DLC は、開発者の焦点を定型コーディング作業から重要な問題解決へ移すことで体験を変える。AI が反復的タスクを処理することで認知負荷を減らし、開発者がより深いビジネス文脈を得て自分の仕事が直接ビジネス価値に影響することを目撃することで満足度が高まる。

## どう始めるか？

3 つの明確な経路で AI-DLC の旅を始められる:

1. 包括的な [AI-DLC ホワイトペーパー](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) を読む
2. [Amazon Q Developer rules](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/context-project-rules.html) と [Kiro custom workflows](https://kiro.dev/docs/steering/) が、組織での AI-DLC 実装にどう役立つかを探る
3. AWS アカウントチームに連絡し、組織の特定ニーズに合わせた AI-DLC の適用について議論する

ソフトウェア開発の未来はここにある。組織は AI を活用して、重要な人間の監督と協業を通じて忠実さと品質を保ちつつ、より速くシステムを構築できる。今日 AI-DLC の旅を始め、AI 駆動イノベーションで開発プラクティスを変革する組織のコミュニティに加わろう。

---

## 著者について

**Raja SP** は AWS の Principal Solutions Architect で、Developer Transformation Programs をリードしている。100 を超える大規模顧客と協働し、モダンアーキテクチャ・プラットフォームエンジニアリングプラクティス・Amazon にインスパイアされた運用モデルでミッションクリティカルなシステムを設計・提供するのを支援してきた。生成 AI がソフトウェア開発のランドスケープを再形成する中、Raja とチームは AI Driven Development Lifecycle (AI-DLC) を作り出した ― AI 時代に大規模チームが本番運用可能なソフトウェアを協業的に構築する方法を再構想する、エンドツーエンドで AI ネイティブなメソドロジー。
