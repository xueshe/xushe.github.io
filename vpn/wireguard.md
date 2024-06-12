# Wireguard搭建VPN

## 服务端

```ini
[Interface]
Address = 192.168.2.1/32
ListenPort = 28385
PrivateKey = <Server private key>

PostUp = iptables -I FORWARD -s 192.168.2.0/24 -i wg0 -d 192.168.2.0/24 -j ACCEPT
PostUp = iptables -I FORWARD -s 192.168.2.0/24 -i wg0 -d 192.168.1.0/24 -j ACCEPT
PostUP = iptables -I FORWARD -s 192.168.1.0/24 -i wg0 -d 192.168.2.0/24 -j ACCEPT

PostDown = iptables -D FORWARD -s 192.168.2.0/24 -i wg0 -d 192.168.2.0/24 -j ACCEPT
PostDown = iptables -D FORWARD -s 192.168.2.0/24 -i wg0 -d 192.168.1.0/24 -j ACCEPT
PostDown = iptables -D FORWARD -s 192.168.1.0/24 -i wg0 -d 192.168.2.0/24 -j ACCEPT

# NAS
[Peer]
PublicKey = <Client public key>
AllowedIPs = 192.168.2.2/32, 192.168.1.0/24

# 其他客户端 ...
[Peer]
PublicKey = <Client public key>
AllowedIPs = 192.168.2.x/32
```

## NAS

```ini
[Interface]
PrivateKey = <Client private key>
Address = 192.168.2.2/32

PostUp = iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -j SNAT --to-source 192.168.1.2
PostDown = iptables -t nat -D POSTROUTING -s 192.168.2.0/24 -j SNAT --to-source 192.168.1.2

[Peer]
PublicKey = <Server public key>
AllowedIPs = 192.168.2.0/24
Endpoint = 1.1.1.1:28385
```

## Peer

```ini
[Interface]
PrivateKey = <Client private key>
Address = 192.168.2.X/32

[Peer]
PublicKey = <Server public key>
AllowedIPs = 192.168.2.0/24, 192.168.1.0/24
Endpoint = 1.1.1.1:28385
```