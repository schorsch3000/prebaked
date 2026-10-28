FROM debian:13
ARG PREBAKE_CONTAINER
COPY --from=ghcr.io/schorsch3000/packagedealer:latest /usr/local/bin/pd /usr/local/bin/pd

WORKDIR /etc/packagedealer/

COPY packages.apt ./$PREBAKE_CONTAINER.apt
COPY packages.pipx ./$PREBAKE_CONTAINER.pipx


RUN pd --clean --update -D /etc/packagedealer/



