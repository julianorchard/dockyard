FROM python:3.12-slim

LABEL org.opencontainers.image.authors="Julian Orchard <hello@julianorchard.co.uk>"
LABEL org.opencontainers.image.source=https://github.com/julianorchard/dockyard

ARG HADOLINT_REPO_BASE_URL=https://github.com/hadolint/hadolint/releases/download
ARG HADOLINT_VERSION=v2.14.0
ARG HADOLINT_BINARY=hadolint-linux-x86_64
ARG HADOLINT_INSTALL_PATH=/usr/local/bin

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl && \
    curl "${HADOLINT_REPO_BASE_URL}/${HADOLINT_VERSION}/${HADOLINT_BINARY}" && \
    curl -sSL "${HADOLINT_REPO_BASE_URL}/${HADOLINT_VERSION}/${HADOLINT_BINARY}" \
      -o ${HADOLINT_INSTALL_PATH}/hadolint && \
    chmod +x ${HADOLINT_INSTALL_PATH}/hadolint && \
    pip install --no-cache-dir pre-commit && \
    apt-get purge -y curl && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

CMD ["pre-commit", "run", "--all-files", "--show-diff-on-failure"]
