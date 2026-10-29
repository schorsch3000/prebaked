# PARENT is set by prebake to <registry>/base:latest.
ARG PARENT
FROM ${PARENT}
ARG PREBAKE_CONTAINER

WORKDIR /etc/packagedealer/
COPY packages.apt ./$PREBAKE_CONTAINER.apt
COPY packages.pipx ./$PREBAKE_CONTAINER.pipx
RUN pd --clean --update -D /etc/packagedealer/
WORKDIR /tmp
COPY dali035.tar.gz .
RUN tar -xzf dali035.tar.gz \
    && rm dali035.tar.gz \
    && cd dali035 \
    && make \
    && cp dali /usr/bin/dali \
    && cd .. \
    && rm -rf dali035














