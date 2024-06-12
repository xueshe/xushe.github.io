## download

https://github.com/fatedier/frp/releases

## client

```PowerShell
frpc tcp -n "tmp-ssh" -i 127.0.0.1 -l 22 -r 44444 -s "36.137.78.193"  -P 47000 -t "1357902468"
```

`````powershell
frpc tcp --proxy_name "tmp-ssh" --local_ip 127.0.0.1 --local_port 22 --remote_port 44444  --server-addr "36.137.78.193"  --server-port 47000 --token "1357902468"
`````

## /etc/systemd/system/frps.service

```ini
[Unit]
Description=Frp Service
After=network.target network-online.target
Requires=network-online.target

[Service]
ExecStart=/usr/local/frp/frps -c /usr/local/frp/frps.toml
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

`````ini
[Unit]
Description=Frp Service
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=simple
ExecStart=/usr/local/frp/frps -c /usr/local/frp/frps.toml
KillSignal=SIGQUIT
TimeoutStopSec=5
KillMode=process
PrivateTmp=true
StandardOutput=syslog
StandardError=inherit

[Install]
WantedBy=multi-user.target
`````

## /etc/systemd/system/frpc.service

```ini
[Unit]
Description=Frpc Client 
After=syslog.target network.target 
Wants=network.target 
 
[Service] 
Type=simple 
ExecStart=/usr/local/frp/frpc -c /usr/local/frp/frpc.toml
 
[Install] 
WantedBy=multi-user.target
```