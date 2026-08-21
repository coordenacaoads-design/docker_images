# Python (Interpretador) - 1o Periodo
FROM python:3.12-slim

LABEL description="Interpretador Python para uso didatico"

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir --upgrade pip setuptools wheel

WORKDIR /workspace

CMD ["python3"]
