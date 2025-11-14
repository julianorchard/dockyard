FROM python:3.12-slim

LABEL org.opencontainers.image.authors="Julian Orchard <hello@julianorchard.co.uk>"
LABEL org.opencontainers.image.source=https://github.com/julianorchard/dockyard

ARG TF_RELEASE_BASE_URL=https://releases.hashicorp.com/terraform/1.13.5/terraform_1.13.5_linux_amd64.zip
ARG TF_VERSION=1.13.5
ARG TF_INSTALL_PATH=/usr/local/bin

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        curl=8.14.1-2 \
        git=1:2.47.3-0+deb13u1 \
        unzip=6.0-29 \
    && curl -sSL "${TF_RELEASE_BASE_URL}" \
        -o "${TF_INSTALL_PATH}/tf.zip" \
    && rm -rf /var/lib/apt/lists/*

WORKDIR $TF_INSTALL_PATH

RUN unzip tf.zip \
    && chmod +x terraform \
    && pip install --no-cache-dir pre-commit==4.3.0 \
    && apt-get purge -y \
        curl \
        unzip

WORKDIR /workspace

CMD ["pre-commit", "run", "--all-files", "--show-diff-on-failure"]
