# Debian Apache (日本環境） #

オフィシャルのhttpd:2.4をベースにApacheコンテナを作成する。

### 調整内容 ###

* locale設定 (ja.utf-8)
* タイムゾーン （Asia/Tokyo）
* 必要なツールのインストール (less, vim, git)
* モジュール追加 （mod_proxy.so, mod_proxy_fcgi.so)
* php-fpmを9000ポートで読み込み
* www-dataユーザーのuidを1000に変更(権限対策)

### イメージの作成方法 ###

```
$ git clone https://github.com/reflet/docker-debian-httpd.git .
$ docker build -t local/debian-httpd .
```

### 起動方法 ###

```
$ docker run --name httpd -d -p 80:80 local/debian-httpd
```

### 接続方法 ###

```
$ docker exec -u "www-data" -it httpd bash
```