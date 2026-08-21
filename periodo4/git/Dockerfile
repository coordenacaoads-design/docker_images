# Git - 4o Periodo
FROM debian:bookworm-slim

LABEL description="Git"

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    openssh-client \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace
CMD ["bash"]
