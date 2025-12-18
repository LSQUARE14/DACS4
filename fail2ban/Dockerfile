FROM debian:stable-slim

RUN apt-get update && \
    apt-get install -y fail2ban iptables && \
    rm -rf /var/lib/apt/lists/*

COPY jail.local /etc/fail2ban/jail.local
COPY filter.d /etc/fail2ban/filter.d

CMD ["fail2ban-server", "-f", "-x", "start"]
