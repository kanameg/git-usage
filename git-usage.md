# git利用方法

## git初期設定

### ユーザー情報の設定
```bash
git config user.name "Your Name"
git config user.email "you@example.com"
```
Gitのユーザー名とメールアドレスを設定します。これらはコミットのメタデータとして使用されます。
ローカルだけでなく、グローバル設定を行う場合は、`--global`オプションを追加します。

### マージの戦略設定
```bash
git config pull.rebase false
```
マージをデフォルトの動作に設定します。これにより、`git pull`を実行した際に、マージコミットが作成されます。


## git基本的な利用方法

### リポジトリのクローン
```bash
git clone <repository-url>
```
レポジトリをローカルにクローンします。

### 変更のステージング
```bash
git add <file>
```
変更をステージングエリアに追加します。特定のファイルを指定するか、すべての変更を追加する場合は`git add .`を使用します

### 変更のコミット
```bash
git commit -m "commit message"
```
ステージングエリアの変更をコミットします。`-m`オプションでコミットメッセージを指定します。

### リモートリポジトリへのプッシュ
```bash
git push origin <branch-name>
```
ローカルの変更をリモートリポジトリにプッシュします。

### リモートリポジトリからのフェッチ
```bash
git fetch -p
```
リモートの変更を確認し、`-p --prune`オプションでリモートになくなった不要なブランチを削除します。

### リモートリポジトリのチェックアウト
```bash
git checkout -b <branch-name> origin/<branch-name>
```
リモートリポジトリのブランチをチェックアウトします。新しいローカルブランチが作成され、リモートブランチが追跡されます。

### ブランチの作成
```bash
git branch <branch-name>
```
新しいブランチを作成します。作成したブランチは、現在のブランチから分岐します。

### ブランチの切り替え
```bash
git checkout <branch-name>
```
指定したブランチに切り替えます。ブランチが存在しない場合は、エラーが発生します。

### ブランチのマージ
```bash
git merge <branch-name>
```
現在のブランチに指定したブランチの変更をマージします。競合が発生した場合は、手動で解決する必要があります。

### ブランチの削除
```bash
git branch -d <branch-name>
```
指定したブランチを削除します。ブランチがマージされていない場合は、`-D`オプションを使用して強制的に削除します。

### リモートブランチの削除
```bash
git push origin --delete <branch-name>
```
リモートリポジトリから指定したブランチを削除します。