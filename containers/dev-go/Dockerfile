# PARENT is set by prebake to <registry>/base:latest.
ARG PARENT
FROM ${PARENT}

# Repeat the full package list and add what you miss. apt skips everything the
# base already has, so adding one tool costs seconds instead of a full rebuild.

RUN wget https://go.dev/dl/go1.27.2.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go1.27.2.linux-amd64.tar.gz && \
    rm go1.27.2.linux-amd64.tar.gz


RUN false
