# gh使い方基礎編

## インストール方法
DockerのLinuxにインストールする場合は以下のような手順でインストールできます。
```
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" > /etc/apt/sources.list.d/github-cli.list
apt-get update
apt-get install -y gh
```

## 基本的な使い方

ghコマンドは、GitHubのリポジトリを操作するためのCLIツールです。基本的な使い方は以下の通りです。

### ログイン方法
コマンドを実行する前に一度ログインする必要があります。以下のコマンド入力後、指示に従いブラウザでGitHubにログインします。
```
gh auth login
```

### リポジトリのクローン
`git`でリポジトリをクローンするのと同様に、`gh`コマンドを使用してGitHubのリポジトリをクローンできます。
URLではなく、レポジトリ名を指定してcloneができるのが特徴です。
```
gh repo clone <リポジトリ名>
```

### イシュー(issue)の作成

```
gh issue create --title "<タイトル>" --body "<説明>"
```

### イシューに関連したブランチの作成
```
gh issue <イシュー番号> develop
```

### プルリクエスト(pr)の作成
```
gh pr create --base <ブランチ名> --head <ブランチ名> --title "<タイトル>" --body "<説明>"
```


### リポジトリの情報取得
```
gh repo view <リポジトリ名>
```