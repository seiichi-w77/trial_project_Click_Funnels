はい、承知いたしました。「Write_User_Onboarding_Documentation」のコマンドを実行します。
以下に、新規ユーザーがMiyabiをスムーズにセットアップし、最初のIssueを処理できるよう導くクイックスタートガイドとオンボーディングドキュメントをMarkdown形式で執筆します。

---

# Miyabi クイックスタートガイド

Miyabiへようこそ！

このガイドは、Miyabiを初めて利用する開発者のためのオンボーディングドキュメントです。
Miyabiは、GitHub Issueを起点として、コーディング、テスト、ドキュメント作成、Pull Requestの提出までを完全自律的に行うAIエージェントフレームワークです。

このガイドを終える頃には、あなたはMiyabiの基本的なセットアップを完了し、最初のGitHub IssueをAIエージェントに処理させる体験をすることができます。

**コアコンセプト: "GitHub as OS"**
- **Input**: GitHub Issue
- **Process**: Miyabi Agent Orchestration
- **Output**: Pull Request

---

## 1. 環境構築

Miyabiを動作させるために、まずはお使いの開発環境を整えましょう。

### 1.1. 前提条件

以下のツールがインストールされ、設定済みであることを確認してください。

- **Git**: バージョン管理の基本です。
- **GitHubアカウント**: IssueやPull Requestを管理します。
- **Rust & Cargo**: MiyabiはRustで構築されています。[公式サイト](https://www.rust-lang.org/tools/install)の手順に従ってインストールしてください。
- **GitHub CLI (`gh`)**: ターミナルからGitHubを操作するための公式ツールです。[公式サイト](https://cli.github.com/)からインストールし、以下のコマンドで認証を済ませてください。
  ```bash
  gh auth login
  ```

### 1.2. Miyabi CLIのインストール

前提条件が整ったら、Cargoを使ってMiyabi CLIをインストールします。

```bash
cargo install miyabi-cli
```
インストール後、`miyabi --version` を実行して正しくインストールされたか確認してください。

### 1.3. 初期設定: APIキーの登録

Miyabiは複数の大規模言語モデル（LLM）とGitHub APIを利用します。動作に必要なAPIキーを設定しましょう。

1.  **GitHub Personal Access Token (PAT) の作成**
    - [GitHubの設定ページ](https://github.com/settings/tokens)にアクセスします。
    - 「Fine-grained tokens」を選択し、新しいトークンを生成します。
    - **Repository permissions** で `Contents`, `Issues`, `Pull requests` に `Read and write` 権限を付与してください。
    - 生成されたトークンを安全な場所にコピーします。

2.  **LLM APIキーの準備**
    Miyabiはタスクに応じて最適なLLMを自動選択する`Hybrid LLM Router`を搭載しています。主要なモデル（例: Claude 3.5 Sonnet）のAPIキーを少なくとも1つ準備してください。
    - Anthropic (Claude)
    - OpenAI (GPT)
    - Google (Gemini)

3.  **環境変数の設定**
    ターミナルで以下の環境変数を設定します。`.zshrc`や`.bashrc`に追記することを推奨します。

    ```bash
    # GitHub Personal Access Token
    export GITHUB_TOKEN="ghp_xxxxxxxxxxxxxxxxxxxx"

    # LLM API Keys (最低1つ設定)
    export ANTHROPIC_API_KEY="sk-ant-xxxxxxxxxxxxxxxxxxxx"
    export OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxx"
    ```
    設定後、`source ~/.zshrc` のようにシェルを再起動するか、新しいターミナルセッションを開始してください。

---

## 2. 最初のIssueを処理する

セットアップが完了しました。いよいよMiyabiに最初の仕事を依頼しましょう。

### 2.1. 準備: 対象リポジトリへ移動

Miyabiに作業させたいプロジェクトのローカルリポジトリへ移動します。
もし、試すためのリポジトリがなければ、新しく作成してクローンしてください。

```bash
# 例
git clone git@github.com:<your-username>/my-test-repo.git
cd my-test-repo
```

### 2.2. Step 1: Issueの作成

Miyabiへの指示はすべてGitHub Issueを通じて行います。`gh`コマンドを使って、簡単な機能追加のIssueを作成してみましょう。

**ポイント**: タイトルは分かりやすく、本文には達成してほしい要件を具体的に記述します。

```bash
gh issue create \
  --title "feat: Add a welcome message to README.md" \
  --body "Please add a new section '## Welcome' to the README.md file with the content 'Welcome to the Miyabi-powered project!'."
```

実行後、Issue番号（例: `#123`）がターミナルに表示されます。この番号を控えておいてください。

### 2.3. Step 2: Miyabiエージェントの起動

いよいよMiyabiを起動します。`miyabi agent run coordinator` コマンドに、先ほど控えたIssue番号を渡します。

```bash
# Issue番号が123の場合
miyabi agent run coordinator --issue 123
```

このコマンドは`CoordinatorAgent`を起動します。このエージェントがIssueを分析し、`CodeGenAgent`（コード生成）、`ReviewAgent`（レビュー）、`DocsAgent`（ドキュメント更新）など、必要な専門エージェントを呼び出してタスクを協調実行させます。

### 2.4. Step 3: 処理のモニタリング

ターミナルには、各エージェントの活動ログがリアルタイムで表示されます。
Miyabiが内部的に新しいブランチを作成し（Git Worktreeを利用）、コードを書き、テストを実行し、コミットする様子を見ることができます。

この間、あなたはコーヒーを淹れて待つだけです。

### 2.5. Step 4: Pull Requestの確認

すべてのタスクが完了すると、Miyabiは自動的にPull Requestを作成し、元のIssueにリンクします。
ターミナルのログが完了したことを示すか、GitHubから通知が届いたら、リポジトリのPull Requestタブを確認しにいきましょう。

そこには、Issueの要件を満たしたコード変更、追加されたテスト、更新されたドキュメントを含む、完璧なPull Requestがあなたを待っています。

内容を確認し、問題がなければマージしてください。
**おめでとうございます！あなたはMiyabiと共に、最初のタスクを完了しました。**

---

## 3. 次のステップ

あなたはMiyabiの基本的な使い方をマスターしました。ここからさらにMiyabiの能力を最大限に引き出すために、以下のドキュメントも参照してください。

-   **Agentの全リストと機能**: Miyabiには21種類以上のエージェントがいます。どのようなエージェントが存在し、何ができるのかを確認しましょう。 (`.claude/agents/specs/*.md`)
-   **ラベルシステムの詳細**: `bug`, `P0-Critical`, `chore`など、57種類のラベルをIssueに付与することで、エージェントの挙動をより細かく制御できます。 (`docs/LABEL_SYSTEM_GUIDE.md`)
-   **Entity-Relationモデル**: Miyabiの根幹をなす設計思想について学びます。 (`docs/ENTITY_RELATION_MODEL.md`)

Miyabiは、あなたの開発プロセスから退屈な作業をなくし、創造的な活動に集中するためのパートナーです。
ようこそ、自律型開発の未来へ。