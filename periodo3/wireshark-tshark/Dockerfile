# Wireshark - 3o Periodo
# Wireshark e uma aplicacao grafica. O equivalente CLI oficial (mesmo motor
# de captura/dissecacao) e o tshark.
FROM ubuntu:22.04

LABEL description="Wireshark (equivalente CLI: tshark)"

ENV DEBIAN_FRONTEND=noninteractive

RUN echo "wireshark-common wireshark-common/install-setuid boolean true" | debconf-set-selections \
    && apt-get update && apt-get install -y --no-install-recommends \
    tshark \
    && rm -rf /var/lib/apt/lists/* \
    && groupadd -f wireshark \
    && usermod -aG wireshark root

WORKDIR /workspace

# Para capturar pacotes de verdade, rode o container com:
#   docker run --cap-add=NET_RAW --cap-add=NET_ADMIN --network host ...
CMD ["tshark", "--version"]
