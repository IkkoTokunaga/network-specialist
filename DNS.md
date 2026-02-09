2026-01-05
# DNS（Domain Name System）
IPアドレスとドメイン名を名前解決を行う機能の総称
```
dig www.google.com

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22192
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1400
;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         75      IN      A       142.250.196.164

;; Query time: 40 msec
;; SERVER: 10.255.255.254#53(10.255.255.254) (UDP)
;; WHEN: Mon Jan 05 10:22:25 JST 2026
;; MSG SIZE  rcvd: 59
```
## id: 22192
基本的にはUDPでの問い合わせのためリクエストとレスポンスを紐付けるためにidを付与している。
ここで見えているidはキャッシュDNSサーバーとクライアントとの間で使用しているidであり、TTLが切れている場合の反復問い合わせで使用しているidまたはport番号はわからない。

## flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, 
| フラグ | 意味        | 立つタイミング      |
| --- | --------- | ------------ |
| qr  | 応答        | レスポンス        |
| rd  | 再帰要求      | クライアント → DNS |
| ra  | 再帰可能      | キャッシュDNS     |
| aa  | 権威応答      | 権威DNS        |
| tc  | 分割        | UDP 512 超過   |
| ad  | DNSSEC検証済 | 検証成功         |
| cd  | 検証しない     | クライアント指定     |
### QUERY
問い合わせ件数
### ANSWER
解決済み件数
### AUTHORITY
権威情報件数
### ADDITIONAL
ANSWER / AUTHORITY とは別の追加レコード

## TTL 75
この数値は権威DNSサーバーに設定されている初期値ではなく、そこから減産されたリアルな残り時間である。
SERVER: 10.255.255.254#53(10.255.255.254) (UDP) とあるようにローカルのキャッシュDNSを使用しているので、そこでのTTL残り時間が表示されている。
実際のTTLの設定を確認するには権威DNSサーバーを直接参照する必要がある。
```
dig google.com NS
;; ANSWER SECTION:
google.com.             285299  IN      NS      ns3.google.com.
google.com.             285299  IN      NS      ns2.google.com.
google.com.             285299  IN      NS      ns4.google.com.
google.com.             285299  IN      NS      ns1.google.com.

dig www.google.com @ns1.google.com
;; ANSWER SECTION:
www.google.com.         300     IN      A       142.250.206.228
```
実際の数値は300であることがわかる。
## DNSリゾルバ
クライアント側でDNSに対して問い合わせを行って、レスポンスを取得してくれる機能のこと

