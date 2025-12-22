FROM debian:stable-slim

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
      openssh-server rsyslog && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/run/sshd /root/.ssh

RUN echo "root:root" | chpasswd

RUN sed -ri 's/^#?PermitRootLogin .*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/^#?PasswordAuthentication .*/PasswordAuthentication yes/' /etc/ssh/sshd_config

EXPOSE 22

CMD ["sh", "-c", "rsyslogd && /usr/sbin/sshd -D -e"]


