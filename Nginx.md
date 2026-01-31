2026-01-31
# Nginx
高性能・軽量なWebサーバ／リバースプロキシ。
## インストール
```
sudo apt install nginx
```
## 設定
```
sudo vi /etc/nginx/conf.d/test.conf
```
conf.d 配下の設定ファイルは全て読み込まれる（*.confのみ）
```
server {
    listen 0.0.0.0:8080;
    server_name _;

    access_log /var/log/nginx/test.access.log;
    error_log  /var/log/nginx/test.error.log;

    location / {
        return 200 "nginx test ok\n";
        add_header Content-Type text/plain;
    }
}
```
ポート番号8080へアクセスする全ての通信に対しての設定
ドメインも全て（_;）
※通常は設定されているドメインを記述する
※検証なのでHTTP200を常に返し、固定のテキストを表示させている
## 起動
```
# 正常性チェック
sudo nginx -t
ginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

# 起動
sudo systemctl start nginx

# 起動確認
sudo systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2026-01-31 23:12:52 JST; 30min ago
       Docs: man:nginx(8)
   Main PID: 14202 (nginx)
      Tasks: 13 (limit: 9330)
     Memory: 11.0M
        CPU: 72ms
     CGroup: /system.slice/nginx.service


## 疎通確認
curl -i http://192.168.125.206:8080
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Sat, 31 Jan 2026 14:44:23 GMT
Content-Type: application/octet-stream
Content-Length: 14
Connection: keep-alive
Content-Type: text/plain

nginx test ok
```
