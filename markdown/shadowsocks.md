# Shadowsocks

## Install

```bash
> sudo apt-get update
> sudo apt-get install --no-install-recommends build-essential autoconf libtool libssl-dev libpcre3-dev libev-dev asciidoc xmlto automake shadowsocks-libev -y
> git clone https://github.com/shadowsocks/simple-obfs.git
> cd simple-obfs && git submodule update --init --recursive
> ./autogen.sh && ./configure && make && sudo make install
> cd ../ && sudo rm -rf simple-obfs
```

 ## Start

```
> sudo vim /etc/shadowsocks-libev/config.json
Copy
---------------------
{
  "server": "0.0.0.0",
  "server_port": 18650,
  "local_port": 1080,
  "password": "Secure",
  "timeout": 60,
  "method": "chacha20",
  "fast_open": true,
  "plugin": "/usr/local/bin/obfs-server --obfs http"
}
---------------------
[Esc+:%d] + i + Paste + [Esc+:wq]
```

## Task
```bash
> sudo systemctl start shadowsocks-libev.service
> sudo systemctl enable shadowsocks-libev.service
> systemctl status shadowsocks-libev.service
> sudo systemctl restart shadowsocks-libev
```

## Google BBR
```bash
> echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
> echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
> sysctl -p && sysctl net.ipv4.tcp_available_congestion_control
> lsmod | grep bbr
```

```
Restart The Server!
```
