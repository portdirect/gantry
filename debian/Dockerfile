ARG FROM=debian:jessie-slim
FROM ${FROM}

ARG PACKAGES
ARG BINARIES

RUN set -ex \
    && apt-get update \
    && apt-get upgrade -y \
    && if [ "x${BINARIES}" != "x" ]; then \
      apt-get install -y curl ca-certificates \
      && for BINARY in ${BINARIES}; do \
        curl -L -o /usr/local/bin/$( echo ${BINARY} | awk -F '/' '{ print $NF }') ${BINARY}; \
      done \
      && chmod +x /usr/local/bin/* \
      && apt-get purge -y --auto-remove curl ca-certificates; \
    fi \
    && if [ "x${PACKAGES}" != "x" ]; then \
      apt-get install -y --no-install-recommends ${PACKAGES}; \
    fi \
    && rm -rf /var/lib/apt/lists/*
