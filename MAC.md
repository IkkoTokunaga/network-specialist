2026-01-10
# MACアドレス
+ ネットワーク機器（NIC）に割り当てられる物理アドレス
+ 例：00:1A:2B:3C:4D:5E
+ L2（データリンク層）で使用
+ ARP、スイッチング、同一ネットワーク内通信で重要
```
ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:15:5d:6b:3b:8c brd ff:ff:ff:ff:ff:ff
```

| 部分      | 意味              |
| ------- | --------------- |
| 上位24bit | **OUI**（ベンダ識別子） |
| 下位24bit | ベンダ内での個体識別      |

ff:ff:ff:ff:ff:ff
ブロードキャスト
## ARPとMACの関係
+ IPは分かるがMACが分からない
+ ARP Request（ブロードキャスト）
+ 対象がARP Reply（ユニキャスト）
+ ARPテーブルにキャッシュ

各端末で受信したらMACヘッダーを剥がして、転送時に付与する。

MACアドレスは簡単に偽装できるので、MACアドレスフィルタリングのセキュリティ効果は限定的