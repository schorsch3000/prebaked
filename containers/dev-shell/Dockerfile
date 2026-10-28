FROM debian:13
COPY init /usr/local/sbin/init
COPY packages.apt /tmp/packages.apt
COPY packages.pipx /tmp/packages.pipx
ENV DEBIAN_FRONTEND=noninteractive
RUN /usr/local/sbin/init
WORKDIR /tmp
