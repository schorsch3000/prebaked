# PARENT is set by prebake to <registry>/base:latest.
ARG PARENT
FROM ${PARENT}

# Repeat the full package list and add what you miss. apt skips everything the
# base already has, so adding one tool costs seconds instead of a full rebuild.

COPY init /usr/local/sbin/init
COPY packages.apt /tmp/packages.apt
COPY packages.pipx /tmp/packages.pipx
ENV DEBIAN_FRONTEND=noninteractive
RUN /usr/local/sbin/init
WORKDIR /tmp
COPY dali035.tar.gz .
RUN tar -xzf dali035.tar.gz \
    && rm dali035.tar.gz \
    && cd dali035 \
    && make \
    && cp dali /usr/local/bin/dali \
    && cd .. \
    && rm -rf dali035

