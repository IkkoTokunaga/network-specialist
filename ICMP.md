2026-01-25
# ICMP（Internet Control Message Protocal）
ネットワーク層の通信確認に使用するプロトコル
トラブルシューティング時にとりあえずpingを行い、ネットワーク層の疎通を確認してうまくいけば、トランスポート層→セッション層→アプリケーション層と検証を行い、逆にうまくいかない場合はネットワーク層→データリンク層→物理層と下位に向かって検証をしていく
```
ping google.com
PING google.com (172.217.174.110) 56(84) bytes of data.
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=1 ttl=117 time=21.5 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=2 ttl=117 time=27.0 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=3 ttl=117 time=23.2 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=4 ttl=117 time=23.4 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=5 ttl=117 time=21.7 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=6 ttl=117 time=22.8 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=7 ttl=117 time=23.9 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=8 ttl=117 time=21.5 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=9 ttl=117 time=23.0 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=10 ttl=117 time=22.0 ms
```
TCPでもUDPでもなくICMPとして存在する
## タイプとコード
+ 「Echo Request」：送信元が宛先に対してICMPを送信する。タイプ8/コード0
+ 「Echo Reply」：通信が成功した場合。タイプ0/コード0
+ 「Request Timeout」：返信なし。タイプ無し/コード無し
+ 「Destination Unreachable」：通信失敗。タイプ3/コード（原因）

| Code   | 意味                                        | 典型シーン       |
| ------ | ----------------------------------------- | ----------- |
| **0**  | Network Unreachable（ネットワーク到達不能）           | ルーティング不可    |
| **1**  | Host Unreachable（ホスト到達不能）                 | ARP失敗など     |
| **2**  | Protocol Unreachable                      | 上位プロトコル未対応  |
| **3**  | **Port Unreachable**                      | UDPでポート未開放  |
| **4**  | Fragmentation Needed and DF set           | MTU不足（DFあり） |
| **5**  | Source Route Failed                       | ソースルーティング失敗 |
| **6**  | Destination Network Unknown               | ネットワーク不明    |
| **7**  | Destination Host Unknown                  | ホスト不明       |
| **8**  | Source Host Isolated                      | 送信元が孤立      |
| **9**  | Network Administratively Prohibited       | 管理的に遮断      |
| **10** | Host Administratively Prohibited          | ホスト単位で遮断    |
| **11** | Network Unreachable for ToS               | ToS理由で不可    |
| **12** | Host Unreachable for ToS                  | ToS理由で不可    |
| **13** | Communication Administratively Prohibited | FW等で通信禁止    |
| **14** | Host Precedence Violation                 | 優先度違反       |
| **15** | Precedence Cutoff in Effect               | 優先度遮断       |
### Port Unreachable
UDPポートが空いていない
### Fragmentation Needed and DF set
DFビットが立っているため分割できない
### Code 0/1
0：ネットワークに問題あり
1：ネットワークは問題なさそうだが、ホストに問題あり
+ 「Redirect」異なるVLANに対して通信する際に別のゲートウェイが存在し、そちらが最適ルートだった場合に、経路変更を促す。
    ※現在ではセキュリティ上の都合でほぼ使われない（MITEの餌食）
