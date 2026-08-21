# Compilador C++ (GCC / MinGW) - 2o Periodo
FROM ubuntu:22.04

LABEL description="GCC/G++ nativo + MinGW-w64 (cross-compiler para Windows)"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    g++ \
    gdb \
    make \
    cmake \
    mingw-w64 \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

CMD ["bash"]
