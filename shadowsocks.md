## 方法1. 使用Docker

https://hub.docker.com/r/mritd/shadowsocks
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

## 方法2. 手动配置

### On server
https://github.com/shadowsocks/shadowsocks-windows/releases
```
pip install shadowsocks
vi /etc/shadowsocks.json
```

写入配置
```
```

使用```chacha20```加密方式需要安装libsodium库
```
wget https://download.libsodium.org/libsodium/releases/LATEST.tar.gz
tar xzvf LATEST.tar.gz
cd libsodium*
./configure
make -j8 && make install
echo /usr/local/lib > /etc/ld.so.conf.d/usr_local_lib.conf
ldconfig
```

启动server
```
ssserver -c /etc/shadowsocks.json -d start
```

安装kcp加速器
```
wget https://raw.githubusercontent.com/kuoruan/kcptun_installer/master/kcptun.sh
chmod +x ./kcptun.sh
./kcptun.sh
```
按照引导设置，客户端端口改为随机端口
加速地址填写```127.0.0.1```及 Shadowsocks 对应端口
无需加密，减轻服务器压力，其余均可默认
记录好生成的配置

### On client
