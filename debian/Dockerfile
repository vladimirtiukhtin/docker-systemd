FROM debian:stretch-slim

ENV container=docker

COPY container.target /etc/systemd/system/container.target

RUN apt update && \
    apt install -y systemd python && \
    ln -sf /etc/systemd/system/container.target /etc/systemd/system/default.target && \
    ln -sf /lib/systemd/systemd /sbin/init

ENTRYPOINT ["/sbin/init"]

CMD ["--log-level=info"]

STOPSIGNAL SIGRTMIN+3
