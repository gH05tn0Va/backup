## Docker
```
docker run -dt --restart=always --name ssclient -p 1080:1080 \
    mritd/shadowsocks -m "ss-local" -s "-s 127.0.0.1 -p 6500 \ 
    -b 0.0.0.0 -l 1080 -m chacha20 -k **** --fast-open" -x \
    -e "kcpclient" -k "-r 138.68.***.***:443 -l :6500 -mode fast2"
```

## Use SwitchyOmega
SOCKS5: `127.0.0.1:1080`
