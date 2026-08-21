# DVC (Data Version Control) - 5o Periodo
FROM python:3.12-slim

LABEL description="DVC"

RUN apt-get update && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir "dvc[all]"

WORKDIR /workspace
CMD ["bash"]
