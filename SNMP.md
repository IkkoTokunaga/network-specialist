2026-02-04
# SNMP（Simple Network Management Protocol）
ネットワーク機器やサーバの性能監視、障害監視で使用する、業界標準の管理プロトコル
## SNMPマネージャ
SNMPエージェントの持っている管理情報を収集、監視するアプリケーションのこと
Zabbixなんかが有名
収集した情報を加工してGUIで見えるかして、分かりやすくする
## SNMPエージェント
SNMPマネージャの要求を受け入れたり、障害を通知したりするプロトコル
### OID（Object Identifer）
SNMPで取得できる1つ1つの値を特定するための番号付き住所
### MIB（Management infomation Base）
OIDに人間の意味を与える説明書
## SNMP Get
SNMPマネージャはSNMPエージェントにOIDを含めた形でGetRequestを送信する
GetRequestはUDPのユニキャストで行われ、そのポート番号は「161」です
それに対してSNMPエージェントは指定されたOIDの値をGetResponseをして返す
次の情報が欲しい場合はSNMPマネージャはGetNextRequestを次にほしいOIDを含めて送信し、SNMPエージェントはGetResponseを返却
## SNMP Set
基本的にはGetと同じ動き
OIDの値を更新して、その値を返却する
## SNMP Trap
SNMPエージェントはOIDの値に特定の変化があった場合に、それを障害と検知してSNMPマネージャにTrapを送信
TrapはUDPのユニキャストで送信され、そのポート番号は「162」
GetとSetはマネージャ発信だったが、Trapはエージェント発信である
