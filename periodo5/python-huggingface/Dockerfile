# Python (com biblioteca Hugging Face) - 5o Periodo
FROM python:3.12-slim

LABEL description="Python + Hugging Face (transformers, datasets, etc.)"

RUN apt-get update && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir \
    torch --index-url https://download.pytorch.org/whl/cpu \
    && pip install --no-cache-dir \
    transformers datasets huggingface_hub accelerate tokenizers

WORKDIR /workspace
CMD ["python3"]
