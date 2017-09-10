ARG FROM=centos:7
FROM ${FROM}

ARG PACKAGES
ARG BINARIES

RUN set -ex \
    && yum upgrade -y \
    && if [ "x${BINARIES}" != "x" ]; then \
      && for BINARY in ${BINARIES}; do \
        curl -L -o /usr/local/bin/$( echo ${BINARY} | awk -F '/' '{ print $NF }') ${BINARY}; \
      done \
      && chmod +x /usr/local/bin/* ; \
    fi \
    && if [ "x${PACKAGES}" != "x" ]; then \
      yum install -y ${PACKAGES}; \
    fi \
    && yum clean all
