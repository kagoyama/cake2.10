# cakephp2.10.24
- docker
- PHP5.6
- apache
- mysql5.7

## 環境構築
まず↓からファイルをダウンロードする
- https://github.com/cakephp/cakephp/releases/tag/2.10.24https://github.com/cakephp/cakephp/releases/tag/2.10.24
- https://github.com/cakephp/cakephp/tags

※このリポジトリはダウンロード後展開済みのもの。

### app/Config/database.php.default
defaultからdatabase.phpを作成し、DBを記載する。

### .htaccess
`RewriteBase /ディレクトリ名`を追加。
`cakephp21`なら以下のように。

```
<IfModule mod_rewrite.c>
	RewriteEngine on
	RewriteBase /cakephp21
```

#### app/.htaccess
同様にapp内にも。（設定不要？）

```
<IfModule mod_rewrite.c>
	RewriteEngine on
	RewriteBase /cakephp21/app
```
### cake server
`cake server`を実行するとローカルサーバーが立つ。

```
$ sudo ./app/Console/cake server
```

## mysqlコンテナ
`docker exec -it {コンテナID} bash`でログイン。
ログイン後、mysqlにログイン。

userとpasswordはdocker-composeで変更可能。
```
// passもuser
$ mysql -u user -p
```
初期設定で`career`DBができているので、データをインポートする。
※SequalAceなどを導入済みなら、使った方が早い
