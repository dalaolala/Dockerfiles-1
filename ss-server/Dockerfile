#
# This is a centos image with Shadowsocks Server
#
# VERSION 0.0.1
#

# Pull base image
FROM centos:latest

# Maintainer
MAINTAINER ansheng ianshengme@gmail.com

# ss variable
ENV PORT 9999
ENV PASSWD ansheng.me
ENV METHOD aes-256-cfb

# Install the required packages
RUN yum install epel-release -y
RUN yum update -y
RUN yum install -y python-pip && yum clean all
RUN pip --no-cache-dir install shadowsocks

ENTRYPOINT /usr/bin/ssserver -p $PORT -k $PASSWD -m $METHOD