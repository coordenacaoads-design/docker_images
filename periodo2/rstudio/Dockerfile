# RStudio Desktop - 2o Periodo
# RStudio Desktop e uma aplicacao grafica. O equivalente containerizavel e
# o RStudio Server, acessivel pelo navegador (http://localhost:8787).
FROM ubuntu:22.04

LABEL description="RStudio (equivalente web: RStudio Server)"

ENV DEBIAN_FRONTEND=noninteractive \
    RSTUDIO_VERSION=2024.09.1-394

RUN apt-get update && apt-get install -y --no-install-recommends \
    r-base \
    gdebi-core \
    wget \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Confira a versao mais recente em https://posit.co/download/rstudio-server/
RUN wget -q https://download2.rstudio.org/server/jammy/amd64/rstudio-server-${RSTUDIO_VERSION}-amd64.deb \
    && gdebi -n rstudio-server-${RSTUDIO_VERSION}-amd64.deb \
    && rm rstudio-server-${RSTUDIO_VERSION}-amd64.deb

RUN useradd -m -s /bin/bash rstudio && echo "rstudio:rstudio" | chpasswd

EXPOSE 8787

CMD ["/usr/lib/rstudio-server/bin/rserver", "--server-daemonize=0"]
