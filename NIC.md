2026-01-14
# NIC （Network Interface Card）
昔は物理的なカードだった。マザボに差し込むもの。現在は組み込まれている、または仮想NIC。
```
ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:15:5d:6b:32:83 brd ff:ff:ff:ff:ff:ff
```
```
ip route
default via 192.168.112.1 dev eth0 proto kernel
192.168.112.0/20 dev eth0 proto kernel scope link src 192.168.125.206
```
メトリック（優先度）は競合がない場合は表示されない。値が低いほうが優先される