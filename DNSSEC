2026-01-05
DNSSEC

```
dig cloudflare.com +dnssec @1.1.1.1

; <<>> DiG 9.18.39-0ubuntu0.22.04.2-Ubuntu <<>> cloudflare.com +dnssec @1.1.1.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46371
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags: do; udp: 1232
;; QUESTION SECTION:
;cloudflare.com.                        IN      A

;; ANSWER SECTION:
cloudflare.com.         300     IN      A       104.16.132.229
cloudflare.com.         300     IN      A       104.16.133.229
cloudflare.com.         300     IN      RRSIG   A 13 2 300 20260106034157 20260104014157 34505 cloudflare.com. cU********************************************************************************************A==

;; Query time: 20 msec
;; SERVER: 1.1.1.1#53(1.1.1.1) (UDP)
;; WHEN: Mon Jan 05 11:42:17 JST 2026
;; MSG SIZE  rcvd: 185
```
ローカルのキャッシュDNSを使用するとDNSSECを使用しない設定になっていることが多いためNS指定にて検証
## ad
Authenticated Data（DNSSEC 検証成功）
## RRSIG
cloudflare.com. 300 IN RRSIG A ...
Aレコードに対する電子署名