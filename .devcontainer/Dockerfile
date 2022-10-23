FROM --platform=arm64 mcr.microsoft.com/devcontainers/typescript-node:16

ARG DEBIAN_FRONTEND=noninteractive
RUN apt update \
    && apt install -y --no-install-recommends \
    curl \
    gettext-base \
    openssl \
    python3-pip \
    sshpass \
    tmux \
    unzip \
    whois \
    && rm -rf /var/lib/apt/lists/* \
    && apt autoremove -y \
    && apt clean -y

ARG ANSIBLE_VERSION
RUN pip install --no-cache-dir ansible==${ANSIBLE_VERSION}

ARG MOLECULE_VERSION
RUN pip install --no-cache-dir molecule[docker]==${MOLECULE_VERSION}