# claudecode-market

ClaudeCode用プラグインマーケットプレイス

## 概要

**claudecode-market** は、Claude Code用のプラグインを発見、共有、インストールできるマーケットプレイスです。このリポジトリを通じて、Claude Codeの機能を拡張する様々なプラグインにアクセスできます。

## マーケットプレイスの追加方法

このマーケットプレイスをClaude Codeに追加するには、以下のコマンドを実行してください：

```bash
# GitHubリポジトリから追加
/plugin marketplace add z-isoda/claudecode-market

# ローカル開発用
/plugin marketplace add ./claudecode-market
```

## プラグインのインストール

マーケットプレイスを追加した後、以下のコマンドでプラグインをインストールできます：

```bash
# プラグイン一覧の確認
/plugin list

# プラグインのインストール
/plugin install <plugin-name>@claudecode-market

# プラグインの有効化
/plugin enable <plugin-name>
```

## 利用可能なプラグイン

現在、以下のプラグインが利用可能です：

<!-- プラグインが追加されたら、ここに一覧を記載します -->

*（準備中）*

## プラグイン開発者向け

### プラグインの追加方法

このマーケットプレイスにプラグインを追加したい場合は、以下の手順に従ってください：

1. **プラグインの作成**
   - 標準的なプラグイン構造に従ってプラグインを作成
   - 必須ファイル: `.claude-plugin/plugin.json`

2. **Pull Requestの作成**
   - `plugins/` ディレクトリにプラグインを追加
   - `.claude-plugin/marketplace.json` にプラグイン情報を追加
   - README.mdのプラグイン一覧を更新

### プラグイン構造

各プラグインは以下の構造に従う必要があります：

```
plugins/<plugin-name>/
├── .claude-plugin/
│   └── plugin.json          # 必須: プラグインメタデータ
├── commands/                # オプション: スラッシュコマンド
├── agents/                  # オプション: エージェント定義
├── skills/                  # オプション: スキル
├── hooks/                   # オプション: フック
├── README.md                # 推奨: 使用方法の説明
└── LICENSE                  # 推奨: ライセンス情報
```

### plugin.jsonの例

```json
{
  "name": "my-plugin",
  "version": "1.0.0",
  "description": "プラグインの説明",
  "author": {
    "name": "あなたの名前",
    "email": "your.email@example.com"
  },
  "license": "MIT",
  "keywords": ["keyword1", "keyword2"],
  "commands": "./commands",
  "skills": "./skills"
}
```

## ディレクトリ構造

```
claudecode-market/
├── .claude-plugin/
│   └── marketplace.json     # マーケットプレイス設定
├── plugins/                 # プラグイン配置ディレクトリ
│   └── (各プラグイン)
├── CLAUDE.md                # Claude Code用ガイダンス
├── README.md                # このファイル
└── LICENSE                  # ライセンス情報
```

## 貢献

プラグインの追加やバグ報告は、GitHubのIssuesやPull Requestsを通じてお願いします。

## ライセンス

このマーケットプレイス自体のライセンスについては、LICENSEファイルを参照してください。各プラグインは独自のライセンスを持つ場合があります。
