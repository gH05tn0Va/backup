## 1. 使用Docker

### On server
```
docker run -dt --restart=always --name ssserver -p 6443:6443 -p 443:6500/udp \
    mritd/shadowsocks -m "ss-server" -s "-s 0.0.0.0 -p 6443 \
    -m chacha20 -k **** --fast-open" -x \
    -e "kcpserver" -k "-t 127.0.0.1:6443 -l :6500 -mode fast2"
```

### On client
```
docker run -dt --restart=always --name ssclient -p 1080:1080 \
    mritd/shadowsocks -m "ss-local" -s "-s 127.0.0.1 -p 6500 \ 
    -b 0.0.0.0 -l 1080 -m chacha20 -k **** --fast-open" -x \
    -e "kcpclient" -k "-r [YOUR_SERVER_IP]:443 -l :6500 -mode fast2"
```

### Use SwitchyOmega
SOCKS5: `127.0.0.1:1080`

## 2. 手动配置

### On server

