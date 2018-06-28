# Shadowsocks Server

> https://hub.docker.com/r/anshengme/ss-server/

## Building & Running

```bash
$ docker build -t ss-server .
$ docker run -d --name ss-server -e PORT=9999 -e PASSWD="ansheng.me" -e METHOD="aes-256-cfb" -p 9999:9999 ss-server
```

## Pull & Running

```bash
$ docker pull anshengme/ss-server
$ docker run -d --name ss-server -e PORT=9999 -e PASSWD="ansheng.me" -e METHOD="aes-256-cfb" -p 9999:9999 anshengme/ss-server
```

> defalut password: ansheng.me
