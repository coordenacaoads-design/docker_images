# n8n - 4o Periodo
# (UiPath Community foi omitido: e um software Windows-only, sem suporte
# Linux/Docker - ver README.)
FROM node:20-slim

LABEL description="n8n - automacao de fluxos de trabalho"

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 build-essential git \
    && rm -rf /var/lib/apt/lists/* \
    && npm install -g n8n

ENV N8N_PORT=5678
EXPOSE 5678

CMD ["n8n", "start"]
