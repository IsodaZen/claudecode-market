# CLAUDE.md

このファイルは、Claude Code (claude.ai/code) がこのリポジトリのコードを扱う際のガイダンスを提供します。

## 要件

- AIはユーザーとのコミュニケーションに日本語を使用する
- 変更の目的が不明確な場合、AIは作業を進める前にユーザーにコンテキストを確認する
- AskUserQuestionを積極的に活用する

## プロジェクト概要

**claudecode-market** は、Claude Code用のプラグインマーケットプレイスです。現在、初期セットアップ段階にあります。

## プロジェクトの目的

このプロジェクトは、Claude Codeユーザーがプラグイン・拡張機能を発見、共有、インストールできるマーケットプレイスプラットフォームを提供することを目指しています。

## Claude Codeプラグイン機能について

### プラグインの種類

Claude Codeでは以下の5つのプラグイン要素をサポートしています：

| プラグイン種類 | 用途 | トリガー |
|---------------|------|---------|
| **スラッシュコマンド** | ユーザーが明示的に実行する命令 | `/command-name` |
| **エージェント** | 特定タスク向けのカスタマイズされたエージェント定義 | 設定または初期化時 |
| **スキル** | モデルが自律的に使用する機能拡張 | Claude が自動判断 |
| **フック** | イベント処理と自動化用のハンドラー | 特定のイベント発生時 |
| **MCPサーバー** | 外部ツールやサービスとの統合 | クエリ時 |

### 標準的なプラグインディレクトリ構造

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json              # プラグインメタデータ（必須）
├── commands/
│   └── command.md               # スラッシュコマンド定義
├── agents/
│   └── agent-name/
│       └── agent.md             # エージェント定義
├── skills/
│   └── skill-name/
│       ├── SKILL.md             # スキル定義（必須）
│       └── examples.md          # 使用例（オプション）
├── hooks/
│   ├── hooks.json               # フック設定
│   └── scripts/
│       └── hook-handler.sh      # フック処理スクリプト
├── README.md
└── LICENSE
```

### プラグインメタデータ（plugin.json）

```json
{
  "name": "plugin-name",
  "version": "1.0.0",
  "description": "プラグインの説明",
  "author": {
    "name": "作成者名",
    "email": "email@example.com"
  },
  "homepage": "https://github.com/username/plugin-name",
  "repository": "https://github.com/username/plugin-name",
  "license": "MIT",
  "keywords": ["keyword1", "keyword2"],
  "commands": "./commands",
  "agents": "./agents",
  "skills": "./skills",
  "hooks": "./hooks/hooks.json"
}
```

### マーケットプレイス構造（marketplace.json）

このマーケットプレイスリポジトリでは、以下の構造でプラグインを管理します：

```json
{
  "name": "claudecode-market",
  "owner": {
    "name": "マーケットプレイス管理者",
    "email": "owner@example.com"
  },
  "version": "1.0.0",
  "description": "Claude Code用のプラグインマーケットプレイス",
  "pluginRoot": "./plugins",
  "plugins": [
    {
      "name": "plugin-name",
      "description": "プラグインの説明",
      "version": "1.0.0",
      "author": "作成者名",
      "license": "MIT",
      "category": "productivity",
      "source": {
        "path": "./plugins/plugin-name"
      }
    }
  ]
}
```

### プラグインのインストール方法

ユーザーは以下のコマンドでこのマーケットプレイスを追加できます：

```bash
# GitHubリポジトリからマーケットプレイスを追加
/plugin marketplace add owner/repo

# ローカル開発用
/plugin marketplace add ./claudecode-market

# プラグインのインストール
/plugin install plugin-name@marketplace-name
```

## 開発状況

このリポジトリは軽量な構成を目指しており、現在は最小限の構造です。このプロジェクトの機能を開発する際：

- プラグインは `./plugins/` ディレクトリに配置
- 各プラグインは独自のディレクトリを持つ
- `.claude-plugin/marketplace.json` でプラグインカタログを管理
- ビルドやデプロイの設定は最小限に抑える
- 静的ファイルとして配布可能な構成を維持

## 次のステップ

このリポジトリに初期構造を追加する際は、以下を考慮してください：

1. **ディレクトリ構造**:
   - `plugins/` - 各プラグインのサブディレクトリ
   - `.claude-plugin/marketplace.json` - マーケットプレイス設定
   - `docs/` - プラグイン作成ガイドなどのドキュメント

2. **プラグインの追加方法**:
   - 各プラグインは標準的なディレクトリ構造に従う
   - `plugin.json` で適切なメタデータを定義
   - README.mdで使用方法を明記

3. **配布方法**:
   - GitHubリポジトリとして公開
   - ユーザーは `/plugin marketplace add` コマンドで追加
   - セマンティックバージョニングを使用

4. **軽量性の維持**:
   - ビルドプロセスは不要
   - 静的ファイルのみで構成
   - Git経由で直接配布可能

## 開発時の注意事項

- すべてのプラグインは独立して動作すること
- プラグイン間の依存関係は最小限に抑える
- セマンティックバージョニング（MAJOR.MINOR.PATCH）を使用
- 各プラグインに適切なLICENSEファイルを含める
- README.mdには明確なインストール手順と使用例を記載
