FROM mcr.microsoft.com/devcontainers/base:2.0.4-noble

RUN apt-get update \
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get install -y --no-install-recommends \
        build-essential \
        ca-certificates \
        curl \
        git \
        jq \
        libsqlite3-dev \
        make \
    && rm -rf /var/lib/apt/lists/*
