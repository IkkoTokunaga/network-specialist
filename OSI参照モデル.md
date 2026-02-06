2026-02-06
# OSI（Open System Interconnection）基本参照モデル
| レイヤー | 層 | 単位 | 説明 |
|:------|:------|:------|:------------|
|7|アプリケーション層|データ（Data）|HTTP / HTTPS, FTP, SMTP, POP3, IMAP, DNS, SNMP|
|6|プレゼンテーション層|データ（Data）|TLS / SSL, MIME, 文字コード（UTF-8 など）|
|5|セッション層|データ（Data）|NetBIOS Session, RPC, SIP|
|4|トランスポート層|セグメント（Segment）<br>データグラム（Datagram）|TCP UDP|
|3|ネットワーク層|パケット（Packet）|IP (IPv4/IPv6), ICMP, IPsec, RIP, OSPF, BGP|
|2|データリンク層|フレーム（Frame）|Ethernet, ARP, VLAN (802.1Q), Wi-Fi (802.11)|
|1|物理層|ビット（Bit）|ケーブル規格, コネクタ, 電圧, 光信号|
