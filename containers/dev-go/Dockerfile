# PARENT is set by prebake to <registry>/base:latest.
ARG PARENT
FROM ${PARENT}
ARG PREBAKE_CONTAINER

# Repeat the full package list and add what you miss. apt skips everything the
# base already has, so adding one tool costs seconds instead of a full rebuild.

ARG GO_VERSION=1.27.2
RUN wget -q https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz && \
    rm -rf /usr/local/go && \
    tar -C /usr/local -xzf go${GO_VERSION}.linux-amd64.tar.gz && \
    rm go${GO_VERSION}.linux-amd64.tar.gz

ENV GOROOT=/usr/local/go \
    GOPATH=/go \
    GOTOOLCHAIN=local
ENV PATH=${GOPATH}/bin:${GOROOT}/bin:${PATH}
RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 1777 "$GOPATH"
