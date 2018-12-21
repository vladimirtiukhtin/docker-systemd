FROM centos

ENV container=docker

COPY container.target /etc/systemd/system/container.target

RUN ln -sf /etc/systemd/system/container.target /etc/systemd/system/default.target

ENTRYPOINT ["/sbin/init"]

CMD ["--log-level=info"]

STOPSIGNAL SIGRTMIN+3
