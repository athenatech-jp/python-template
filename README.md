# python-template

Pythonプロジェクト用のテンプレートリポジトリ

## ファイル構成

```
.
├── .github
│   └── workflows
│       ├── claude-review.yml
│       ├── ruff.yml
│       └── type-check.yml
├── src
│   ├── __init__.py
│   └── sample.py
├── tests
│   ├── __init__.py
│   └── test_sample.py
├── .gitignore
├── .pre-commit-config.yaml
├── Makefile
├── README.md
├── pyproject.toml
└── uv.lock
```

## Setup

1. [Installation | uv](https://docs.astral.sh/uv/getting-started/installation/) を参考にして、 `uv` コマンドをインストールする

```bash
# macOS and Linux
curl -LsSf https://astral.sh/uv/install.sh | less
```

2. 依存関係のインストール / pre-commitの設定

- 下記を実行すると、依存関係のインストールと pre-commit の設定が実行されます。
- `uv sync` と `uv run pre-commit install` を実行しても同じです。

```bash
make init
```

3. Claude Code用に API Key を設定する

- 以下のコマンドを実行すると `~/.claude/settings.json` に Claude API Key が設定されます。
- **すでに設定されている場合は上書きされます。**

```bash
make setup-claude-api-key
```

※参考: [\[Claude Code\]任意のAPIを設定する](https://zenn.dev/aew2sbee/articles/claude-code-api-setting)

練習用に編集してみる

## Pull Request で Claude によるコードレビューを実行する

- Pull Request 内で @claude とメンションするとレビューが実行されます。

> \[!IMPORTANT\]
>
> - AnthropicのAPIキーが必要です。GitHub Secretsに `ANTHROPIC_API_KEY` を設定してください。
> - [GitHub App](https://github.com/organizations/athenatech-jp/settings/installations/68033881)ページで、リポジトリアクセスを許可してください。
