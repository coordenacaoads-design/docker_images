# VS Code - 1o Periodo
# GUI nao esta disponivel dentro de um container por padrao, entao usamos o
# code-server: o proprio VS Code rodando em modo servidor, acessivel pelo
# navegador (http://localhost:8080).
FROM ubuntu:22.04

LABEL description="VS Code via code-server (acesso pelo navegador)"

ENV DEBIAN_FRONTEND=noninteractive \
    HOME=/home/coder

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    ca-certificates \
    git \
    sudo \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://code-server.dev/install.sh | sh

RUN useradd -m -s /bin/bash coder \
    && echo "coder ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER coder
WORKDIR /home/coder/project

EXPOSE 8080

# Defina a senha de acesso na hora do "docker run" com -e PASSWORD=suasenha
ENTRYPOINT ["code-server", "--bind-addr", "0.0.0.0:8080"]
