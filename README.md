# cakephp2.10.24
- docker
- PHP5.6
- apache
- mysql5.7

## 環境構築（基礎）
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

## 環境構築（docker）
`docker-compose`を行い、`localhost:8021`にアクセスする。

```
$ docker-compose up -d --build
```

- ドキュメントルートを`app/webroot`にしているので`cake server`不要。

## mysqlコンテナ
`docker exec -it cake21 bash`でコンテナへ入る。
その後、mysqlにログイン。

userとpasswordはdocker-composeで変更可能。
```
$ docker ps

CONTAINER ID   IMAGE        COMMAND                  CREATED         STATUS          PORTS                  NAMES
62e831116975   cake21-web   "docker-php-entrypoi…"   2 minutes ago   Up 2 minutes    0.0.0.0:8021->80/tcp   cake21
$ docker exec -it cake21 bash

// コンテナ内
// passもuser
$ mysql -u user -p
```
※SequalAceなどを導入済みなら、使った方が早い
