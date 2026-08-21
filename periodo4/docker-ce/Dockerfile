# Docker Community Edition - 4o e 5o Periodo
# Roda o Docker Engine (dockerd) dentro do proprio container
# ("Docker-in-Docker"). Precisa ser executado com --privileged.
# Alternativa mais leve: usar so a CLI (docker-ce-cli) e montar o socket
# do Docker do host com -v /var/run/docker.sock:/var/run/docker.sock
# (ver README para detalhes das duas opcoes).
FROM ubuntu:22.04

LABEL description="Docker Engine + CLI"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates curl gnupg \
    && install -m 0755 -d /etc/apt/keyrings \
    && curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc \
    && chmod a+r /etc/apt/keyrings/docker.asc \
    && echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
      $(. /etc/os-release && echo $VERSION_CODENAME) stable" \
      > /etc/apt/sources.list.d/docker.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
      docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin \
    && rm -rf /var/lib/apt/lists/*

VOLUME /var/lib/docker

CMD ["dockerd"]
