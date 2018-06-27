# CentOS SSH

## Building & Running

```bash
$ docker build -t anshengme/centos-ssh .
$ docker run -d -p 22:22 anshengme/centos-ssh
```

## Test

```bash
$ ssh root@127.0.0.1
```