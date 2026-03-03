2026-01-25
# ICMP（Internet Control Message Protocal）
IP通信のエラー通知や制御情報を伝えるためのプロトコル
トラブルシューティング時にとりあえずpingを行い、ネットワーク層の疎通を確認してうまくいけば、トランスポート層→セッション層→アプリケーション層と検証を行い、逆にうまくいかない場合はネットワーク層→データリンク層→物理層と下位に向かって検証をしていく
```
ping google.com
PING google.com (172.217.174.110) 56(84) bytes of data.
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=1 ttl=117 time=21.5 ms
64 bytes from nrt12s28-in-f14.1e100.net (172.217.174.110): icmp_seq=2 ttl=117 time=27.0 ms
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
## エラーの実例
```
ping -M do -s 2000 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 2000(2028) bytes of data.
ping: local error: message too long, mtu=1500
ping: local error: message too long, mtu=1500
```
pingは分かりやすいようにメッセージに変換して表示していますね！
いちいち調べなくてもいいから助かる！
## ICMPヘッダ
TCPやUDPのようにデータを送っているわけではない
イーサネットフレームとIPヘッダーがあり、その中にICMPヘッダー+データ（Type 8: Echo Request）でリクエストしている
| フィールド           | 内容              |
| --------------- | --------------- |
| Type            | 8（Echo Request） |
| Code            | 0               |
| Identifier      | 識別番号            |
| Sequence Number | 連番              |
| Data            | 任意データ           |
## PMTUDブラックホール問題
送信側でIPヘッダーに「DF＝１」（分割禁止）を立てて送信し、かつフラグメントが起きた場合にICMPで適切なMTUの値を通知するが、FWで遮断した場合はタイムアウトとなって原因が分からず再送が繰り返されるといった問題
特にIPv6ではフラグメント禁止なのでICMP必須
FWのルールで全てのICMPの通信を遮断するのではなく、必要なICMPを許可する運用が正しい
- Echo Reply（DDoS対策で制限を入れる）
- Destination Unreachable
- Fragmentation Needed
- Time Exceeded