#
# This is a centos image with SSH
#
# VERSION 0.0.1
#

# Pull base image
FROM centos:latest

# Maintainer
MAINTAINER ansheng ianshengme@gmail.com

# Profile variable
ENV SSHD_CONF /etc/ssh/sshd_config

# Install the required packages
RUN yum install epel-release -y
RUN yum update -y
RUN yum install openssh-server openssh-clients -y
RUN yum install vim net-tools -y

# Configuration SSH Server
RUN sed -i 's@HostKey /etc/ssh/ssh_host_ecdsa_key@#HostKey /etc/ssh/ssh_host_ecdsa_key@g' $SSHD_CONF \
    && sed -i 's@HostKey /etc/ssh/ssh_host_ed25519_key@#HostKey /etc/ssh/ssh_host_ed25519_key@g' $SSHD_CONF \
    && sed -i 's@#HostKey /etc/ssh/ssh_host_dsa_key@HostKey /etc/ssh/ssh_host_dsa_key@g' $SSHD_CONF \
    && sed -i 's@#UseDNS yes@UseDNS no@g' $SSHD_CONF \
    && ssh-keygen -P "" -t dsa -f /etc/ssh/ssh_host_dsa_key \
    && ssh-keygen -P "" -t rsa -f /etc/ssh/ssh_host_rsa_key

# Clean up cache
RUN yum clean all && rm -f /tmp/*

# Set the root password
RUN echo 'ansheng.me' | passwd root --stdin

ENTRYPOINT ["/usr/sbin/sshd", "-D"]