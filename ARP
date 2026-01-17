2026-01-17
# ARP（Adress Resolusiton Protocol）
IPアドレスからMACアドレスを求める

宛先IPアドレスがどのポートにいるかブロードキャストでARP通信を送り、該当IPアドレスの端末はユニキャストでMACアドレスを送り返す

ARPテーブルの確認
```
arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.112.1            ether   00:15:5d:f5:23:41   C                     eth0
```
または
```
ip neigh
192.168.112.1 dev eth0 lladdr 00:15:5d:f5:23:41 STALE
```

ブロードキャストで宛先IPアドレスを探索するので毎回通信していたら回線が込み合ってしまう。
よって以下
キャッシュ機能を持ち、ARPテーブルに一定期間保持を行う。
