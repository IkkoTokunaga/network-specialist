2026-01-05

## DNSレコードの種類
- A / AAAA: 名前 → IP
- CNAME: 別名
- MX: メール配送先
- TXT: 認証・検証用
- NS: 権威DNS
- SOA: ゾーン管理情報
- RRSIG / DNSKEY / DS: DNSSEC用
### A
```
dig google.com A
google.com.             134     IN      A       142.251.42.206
```
### AAAA
```
dig google.com AAAA
google.com.             261     IN      AAAA    2404:6800:4004:827::200e
```
### MX
```
dig google.com MX
;; ANSWER SECTION:
google.com.             300     IN      MX      10 smtp.google.com.

;; ADDITIONAL SECTION:
smtp.google.com.        261     IN      A       142.250.157.27
smtp.google.com.        261     IN      A       142.251.8.27
smtp.google.com.        261     IN      A       142.251.8.26
smtp.google.com.        261     IN      A       142.251.170.27
smtp.google.com.        261     IN      A       142.251.170.26
```
### TXT
```
dig google.com txt
google.com.             694     IN      TXT     "docusign=05958488-4752-4ef2-95eb-aa7ba8a3bd0e"
google.com.             694     IN      TXT     "facebook-domain-verification=22rm551cu4k0ab0bxsw536tlds4h95"
google.com.             694     IN      TXT     "v=spf1 include:_spf.google.com ~all"
google.com.             694     IN      TXT     "google-site-verification=TV9-DBe4R80X4v0M4U_bd_J9cpOJM0nikft0jAgjmsQ"
google.com.             694     IN      TXT     "google-site-verification=wD8N7i1JTNTkezJ49swvWW48f8_9xveREV4oB-0Hf5o"
google.com.             694     IN      TXT     "globalsign-smime-dv=CDYX+XFHUw2wml6/Gb8+59BsH31KzUr6c1l2BPvqKX8="
google.com.             694     IN      TXT     "cisco-ci-domain-verification=47c38bc8c4b74b7233e9053220c1bbe76bcc1cd33c7acf7acd36cd6a5332004b"
google.com.             694     IN      TXT     "onetrust-domain-verification=de01ed21f2fa4d8781cbc3ffb89cf4ef"
google.com.             694     IN      TXT     "MS=E4A68B9AB2BB9670BCE15412F62916164C0B20BB"
google.com.             694     IN      TXT     "apple-domain-verification=30afIBcvSuDV2PLX"
google.com.             694     IN      TXT     "google-site-verification=4ibFUgB-wXLQ_S7vsXVomSTVamuOXBiVAzpR5IZ87D0"
google.com.             694     IN      TXT     "docusign=1b0a6754-49b1-4db5-8540-d2c12664b289"
```
### NS
```
dig google.com NS
;; ANSWER SECTION:
google.com.             308434  IN      NS      ns3.google.com.
google.com.             308434  IN      NS      ns1.google.com.
google.com.             308434  IN      NS      ns2.google.com.
google.com.             308434  IN      NS      ns4.google.com.

;; ADDITIONAL SECTION:
ns2.google.com.         137260  IN      A       216.239.34.10
ns2.google.com.         137129  IN      AAAA    2001:4860:4802:34::a
ns4.google.com.         137129  IN      A       216.239.38.10
ns4.google.com.         137164  IN      AAAA    2001:4860:4802:38::a
ns3.google.com.         137276  IN      A       216.239.36.10
ns3.google.com.         137226  IN      AAAA    2001:4860:4802:36::a
ns1.google.com.         137114  IN      A       216.239.32.10
ns1.google.com.         137170  IN      AAAA    2001:4860:4802:32::a
```
