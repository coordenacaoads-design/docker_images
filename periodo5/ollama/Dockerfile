# Ollama - 5o Periodo
FROM ubuntu:22.04

LABEL description="Ollama (execucao local de LLMs)"

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl ca-certificates \
    && curl -fsSL https://ollama.com/install.sh | sh \
    && rm -rf /var/lib/apt/lists/*

EXPOSE 11434

ENTRYPOINT ["ollama"]
CMD ["serve"]
