# python-template

Pythonプロジェクト用のテンプレートリポジトリ

## ファイル構成

```
.
├── .agents            # エージェント用の設定・スキル置き場 (空)
├── .claude -> .agents # symlink
├── .github
│   ├── pull_request_template.md
│   └── workflows
│       ├── claude-review.yml  # label 付与で Claude レビューを実行
│       ├── claude.yml         # @claude メンションで Q&A を実行
│       ├── pytest.yml
│       ├── ruff-check.yml
│       └── type-check.yml
├── src
│   └── __init__.py
├── tests
│   └── __init__.py
├── .env.example
├── .gitignore
├── .pre-commit-config.yaml
├── AGENTS.md
├── CLAUDE.md -> AGENTS.md # symlink
├── README.md
├── Taskfile.yml
└── pyproject.toml
```

> [!NOTE]
> `uv.lock` はテンプレート使用時に最新バージョンで解決できるよう、意図的にコミットしていません。
> `uv sync` を実行するとロックファイルが生成されるので、プロジェクトではそのままコミットしてください。
> また `pyproject.toml` の `exclude-newer = "1 week"` により、公開から 1 週間未満のバージョンは解決対象から除外されます。

> [!TIP]
> `AGENTS.md` や `.agents/` の内容はテンプレートの初期値です。プロジェクトに合わせて自由に変更・追記してください。

- 環境変数が必要な場合は `.env.example` をコピーして `.env` を作成してください (`.env` は gitignore 済み)。
- テストが 1 件も無い場合でも pytest の CI は落ちないようにしています (exit code 5 を成功扱い)。テストを書いたら通常どおり判定されます。

## Setup

1. [Installation | uv](https://docs.astral.sh/uv/getting-started/installation/) を参考にして、 `uv` コマンドをインストールする

```bash
# macOS and Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. [Installation | Task](https://taskfile.dev/installation/) を参考にして、 `task` コマンドをインストールする

```bash
# macOS (Homebrew)
brew install go-task/tap/go-task
```

3. 依存関係のインストール / pre-commitの設定

- 下記を実行すると、依存関係のインストールと pre-commit の設定が実行されます。
- `uv sync` と `uv run pre-commit install` を実行しても同じです。

```bash
task init
```

## タスク一覧

```bash
task init                  # 依存関係のインストールと pre-commit の設定
task fmt                   # コードのフォーマットと lint (自動修正)
task ty                    # 型チェック
task test                  # pytest の実行
task pre-commit            # 全ファイルに対して pre-commit hooks を実行
```

## Claude による GitHub 連携

> [!IMPORTANT]
>
> - AnthropicのAPIキーが必要です。GitHub Secretsに `ANTHROPIC_API_KEY` を設定してください。
> - [GitHub App](https://github.com/organizations/athenatech-jp/settings/installations/68033881)ページで、リポジトリアクセスを許可してください。

### PR レビュー (claude-review.yml)

- Pull Request に `claude-review` label を付与するとレビューが実行され、指摘が inline comment として投稿されます。
- レビュー完了後 (失敗時も) label は自動で外れるので、再度 label を付与すると再レビューできます。

### Q&A (claude.yml)

- Issue / PR のコメントで `@claude` とメンションすると、質問への回答が実行されます。
- ファイル編集や git 操作は禁止しているため、回答専用です。
