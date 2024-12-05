FROM alpine:3.20

LABEL org.opencontainers.image.authors="Julian Orchard <hello@julianorchard.co.uk>"
LABEL org.opencontainers.image.source=https://github.com/julianorchard/dockyard

RUN apk add --no-cache libintl=0.22.5-r0 && \
    apk add --no-cache -t build_deps gettext=0.22.5-r0
