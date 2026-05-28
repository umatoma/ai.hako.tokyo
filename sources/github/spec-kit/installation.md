---
title: "Spec Kit インストールガイド"
title_original: "Installation Guide | Spec Kit Documentation"
source_url: https://github.github.com/spec-kit/installation.html
captured_at: 2026-05-28
published_at: 2025-09-02
author: GitHub (github/spec-kit メンテナー)
original_language: en
tags: [spec-kit, installation, cli, uv, pipx, setup]
---

> 取り込みメモ: 公式ドキュメントサイトの Installation Guide の日本語訳。WebFetch で取得したものを翻訳。コードブロック・コマンド・パスは原文のまま残す。

# インストールガイド

## 前提条件

- **Linux/macOS**（または Windows; WSL なしの PowerShell スクリプトも対応）
- AI コーディングエージェント: Claude Code、GitHub Copilot、Codebuddy CLI、Gemini CLI、または Pi Coding Agent
- パッケージ管理は **uv**（推奨）または **pipx**（永続インストール）
- Python 3.11+
- Git

## インストール

> **重要**
> 「Spec Kit の唯一公式かつ保守されているパッケージは、github/spec-kit GitHub リポジトリから来るものだけ。」

### 永続インストール（推奨）

一度インストールしてどこからでも使う。`vX.Y.Z` を Releases のタグに置き換える:

```
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z
```

次にプロジェクトを初期化:

```
specify init <PROJECT_NAME> --integration copilot
```

### ワンタイム利用

インストールせず直接実行 — One-time usage (uvx) ガイドを参照。

### 別のパッケージマネージャ

- **pipx** — pipx インストールガイドを参照
- **エンタープライズ / エアギャップ** — Air-gapped インストールガイドを参照

### Specify 連携

対話型ターミナルでは、初期化時にコーディングエージェント連携を選ぶよう促される。非対話セッションでは、`--integration` を渡さない限り GitHub Copilot がデフォルトになる。

事前に連携を明示する:

```
specify init <project_name> --integration claude
specify init <project_name> --integration gemini
specify init <project_name> --integration copilot
specify init <project_name> --integration codebuddy
specify init <project_name> --integration pi
```

### スクリプトタイプ指定 (Shell vs PowerShell)

すべての自動化スクリプトは Bash (`.sh`) と PowerShell (`.ps1`) 両方のバリアントを持つ。

自動動作:

- Windows のデフォルト: `ps`
- それ以外のデフォルト: `sh`
- 対話モードでは `--script` を渡さなければプロンプトされる

スクリプトタイプを強制する:

```
specify init <project_name> --script sh
specify init <project_name> --script ps
```

### エージェントツール確認を無視する

```
specify init <project_name> --integration claude --ignore-agent-tools
```

## 検証

インストール後、実行:

```
specify version
```

初期化後、以下のコマンドが利用可能になる:

- `/speckit.specify` — 仕様を作成
- `/speckit.plan` — 実装計画を生成
- `/speckit.tasks` — 実行可能なタスクに分解

スクリプトはバリアント別サブディレクトリにインストールされる:

- `.specify/scripts/bash/` — `.sh` スクリプト（Linux/macOS のデフォルト）
- `.specify/scripts/powershell/` — `.ps1` スクリプト（Windows のデフォルト）

## トラブルシューティング

### エンタープライズ / エアギャップ環境

PyPI や GitHub アクセスがブロックされている環境では、移植可能な wheel バンドルを作成するための Enterprise / Air-Gapped Installation ガイドを参照。

### Linux での Git Credential Manager

Linux での Git 認証問題には、Air-Gapped Installation ガイドが Git Credential Manager のセットアップ手順を提供している。
