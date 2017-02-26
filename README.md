# Debian8 Apache (日本環境） #

オフィシャルのhttpd:2.4を元に日本環境の調整を行いました。

### 調整内容 ###

* locale設定 (ja.utf-8)
* タイムゾーン （Asia/Tokyo）
* 必要なツールのインストール (less vim git)
* モジュール追加 （mod_proxy.so, mod_proxy_fcgi.so)
* php-fpmを9000ポートで読み込み

### 使い方 ###

下記のコマンドにてコンテナを起動します。

```
$ docker pull reflet/debian8-httpd
$ docker run --name httpd -d -p 80:80 local/debian8-httpd
$ docker ps -a
$ curl http://192.168.33.10/
```

### メンテナンス ###

下記のコマンドにてソースのダウンロードとイメージの構築を実行します。

```
$ git clone https://github.com/reflet/docker-debian-httpd.git .
$ docker build -t reflet/debian8-httpd .
$ docker login
$ docker push reflet/debian8-httpd
```

### コンテナ操作 ( EXEC ） ###

コンテナ内に入って操作したい場合は、下記コマンドにて接続ください。
※操作を終了する場合は、「exit」でコンソールを抜けられます。

```
$ docker exec -u "www-data" -it httpd bash
```
