# PARENT is set by prebake to <registry>/base:latest.
ARG PARENT
FROM ${PARENT}
ARG PREBAKE_CONTAINER
# Repeat the full package list and add what you miss. apt skips everything the
# base already has, so adding one tool costs seconds instead of a full rebuild.

WORKDIR /etc/packagedealer/
COPY packages.apt ./$PREBAKE_CONTAINER.apt
COPY packages.pipx ./$PREBAKE_CONTAINER.pipx
RUN pd --clean --update -D /etc/packagedealer/

WORKDIR /tmp