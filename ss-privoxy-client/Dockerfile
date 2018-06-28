#
# This is a centos image with ss privoxy client
#
# VERSION 0.0.1
#

# Pull base image
FROM anshengme/centos-ssh:latest

# Maintainer
MAINTAINER ansheng ianshengme@gmail.com

# Install the required packages
RUN yum install -y python-pip privoxy supervisor
RUN pip --no-cache-dir install shadowsocks

# Configuration Shadowsocks
COPY shadowsocks.json /etc/

# Configuration Privoxy
RUN mv /etc/privoxy/config /etc/privoxy/config_bak
RUN echo "listen-address  0.0.0.0:8118" >> /etc/privoxy/config
RUN echo "forward-socks5t / 0.0.0.0:1080 ." >> /etc/privoxy/config

# Configuration Supervisor
RUN sed -i 's#nodaemon=false#nodaemon=true#g' /etc/supervisord.conf
COPY supervisor.ini /etc/supervisord.d/

# Mapping port
EXPOSE 1080 8118

# Clean up cache
RUN yum clean all && rm -f /tmp/*

ENTRYPOINT ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]