FROM debian:13
ARG PREBAKE_CONTAINER
COPY --from=ghcr.io/schorsch3000/packagedealer:latest /usr/local/bin/pd /usr/local/bin/pd
RUN echo 'Acquire::http::Proxy "http://172.17.0.1:3142";' > /etc/apt/apt.conf.d/01proxy
RUN  sed -i '/^Components:/ {/contrib/! s/$/ contrib/; /non-free/! s/$/ non-free/; /non-free-firmware/! s/$/ non-free-firmware/}' /etc/apt/sources.list.d/debian.sources

COPY debian.list /etc/apt/sources.list.d/debian.list



WORKDIR /etc/packagedealer/

COPY packages.apt ./$PREBAKE_CONTAINER.apt
COPY packages.pipx ./$PREBAKE_CONTAINER.pipx


RUN pd --clean -D /etc/packagedealer/


WORKDIR /tmp
#TODO use ghri
RUN wget https://github.com/git-bug/git-bug/releases/download/v0.11.0/git-bug_0.11.0_linux_amd64.deb -O /tmp/git-bug.deb && \
    dpkg -i /tmp/git-bug.deb && \
    rm /tmp/git-bug.deb



