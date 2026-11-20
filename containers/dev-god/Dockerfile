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
