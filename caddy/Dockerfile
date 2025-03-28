# syntax=docker/dockerfile:1

ARG VERSION
FROM --platform=${BUILDPLATFORM} caddy:${VERSION}-alpine AS builder

ARG TARGETPLATFORM
ARG BUILDPLATFORM
ARG TARGETOS
ARG TARGETARCH

# Install xcaddy
RUN apk add --no-cache curl git go && \
    curl -fsSL https://github.com/caddyserver/xcaddy/releases/latest/download/xcaddy-linux-amd64 -o /usr/bin/xcaddy && \
    chmod +x /usr/bin/xcaddy

RUN GOOS=${TARGETOS} GOARCH=${TARGETARCH} xcaddy build \
    --with github.com/caddy-dns/cloudflare

FROM --platform=${TARGETPLATFORM} caddy:${VERSION}-alpine

COPY --from=builder /usr/bin/caddy /usr/bin/caddy