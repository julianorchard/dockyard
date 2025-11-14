FROM python:3.12-slim

LABEL org.opencontainers.image.authors="Julian Orchard <hello@julianorchard.co.uk>"
LABEL org.opencontainers.image.source=https://github.com/julianorchard/dockyard

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        curl=8.14.1-2 \
        git=1:2.47.3-0+deb13u1 \
    && pip install --no-cache-dir pre-commit==4.3.0 \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

CMD ["pre-commit", "run", "--all-files", "--show-diff-on-failure"]
