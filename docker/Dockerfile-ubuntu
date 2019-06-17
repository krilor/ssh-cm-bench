FROM ubuntu:bionic

LABEL maintainer="krilor"

RUN apt update
RUN apt -y install openssh-server
RUN mkdir -p /var/run/sshd

COPY sshd_config /etc/ssh/sshd_config
RUN passwd -d root

COPY run.sh /run.sh
RUN chmod +x /run.sh

EXPOSE 22
CMD ["/run.sh"]
