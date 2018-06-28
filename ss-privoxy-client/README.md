# SS Privoxy Client

带`privoxy`代理的`ss客户端

## 构建

构建之前，请修改`shadowsocks.json`配置

```bash
$ git clone https://github.com/anshengme/Dockerfiles.git
$ cd Dockerfiles/ss-privoxy-client
$ docker build -t ss-privoxy-client .
```

## 运行

```bash
$ docker run --name ss-privoxy-client -d -p 22:22 -p 1080:1080 -p 8118:8118 ss-privoxy-client
```

`SSH`用户为`root`，登录密码为`ansheng.me`

## 使用Privoxy

```bash
# vi /etc/profile 在最后添加如下信息
PROXY_HOST=127.0.0.1
export all_proxy=http://$PROXY_HOST:8118
export ftp_proxy=http://$PROXY_HOST:8118
export http_proxy=http://$PROXY_HOST:8118
export https_proxy=http://$PROXY_HOST:8118
export no_proxy=localhost,172.16.0.0/16,192.168.0.0/16.,127.0.0.1,10.10.0.0/16

# 重载环境变量
source /etc/profile
```
