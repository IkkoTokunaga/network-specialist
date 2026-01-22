2026-01-14
# tcpdump
```
22:33:56.482566 00:15:5d:1f:77:c6 (oui Unknown) > 00:15:5d:6b:32:83 (oui Unknown), ethertype IPv4 (0x0800), length 105: lb-140-82-112-22-iad.github.com.https > 192.168.125.206.48484: Flags [P.], seq 3633706273:3633706312, ack 4186205663, win 70, options [nop,nop,TS val 2097750463 ecr 4042260430], length 39
```
観測するとGithubから定期的にHTTPS通信がされていることがわかる。
おそらく自動Fetch機能など？

[Ethernet情報], [EtherType情報], [IP/TCP情報]
```
00:15:5d:1f:77:c6 > 00:15:5d:6b:32:83 (oui Unknown),
```
送信元MACアドレス > 宛先MACアドレス
```
lb-140-82-112-22-iad.github.com.https > 192.168.125.206.48484
```
githubからHTTPS通信が、手元の端末に届いている
HTTPSなので中身は暗号化されており、確認不可

```
22:54:50.607729 IP tokunaga.mshome.net.51863 > 239.255.255.250.3702: UDP, length 656
```
UDPバージョン