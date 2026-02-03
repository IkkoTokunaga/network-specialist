2026-02-03
# NTP（Network Time Protocol）
機器の時刻を合わせるためのプロトコル
複数の機器が絡み合う障害が発生した場合に、その障害の流れを時系列で理解することが重要であり、異なる機器での時刻が同期されていることが前提である。
## NTP query
今何時ですか？をNTPサーバに問い合わせる
デフォルトポートは123
## NTP Reply
```
$ timedatectl
               Local time: 水 2026-02-04 00:06:48 JST
           Universal time: 火 2026-02-03 15:06:48 UTC
                 RTC time: 火 2026-02-03 15:06:48
                Time zone: Asia/Tokyo (JST, +0900)
System clock synchronized: yes
              NTP service: inactive
          RTC in local TZ: no
```
## うるう秒
Stratum0は数年に一回のスパンで1秒追加したり、スキップしたりする
ベンダーが用意したNTPサーバを使用する場合にはうるう秒に対応しているか確認をしておく