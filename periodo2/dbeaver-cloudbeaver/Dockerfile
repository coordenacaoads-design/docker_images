# DBeaver - 2o Periodo
# DBeaver Desktop e uma aplicacao grafica sem versao CLI oficial. O
# equivalente containerizavel e o CloudBeaver CE: o mesmo motor do DBeaver
# Community, acessivel pelo navegador (http://localhost:8978).
FROM eclipse-temurin:17-jre-jammy

LABEL description="DBeaver (equivalente web: CloudBeaver CE)"

# Confira a versao mais recente em https://github.com/dbeaver/cloudbeaver/releases
# e ajuste abaixo se o link tiver mudado.
ENV CLOUDBEAVER_VERSION=24.2.2

RUN apt-get update && apt-get install -y --no-install-recommends \
    wget \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /opt/cloudbeaver

RUN wget -q https://github.com/dbeaver/cloudbeaver/releases/download/${CLOUDBEAVER_VERSION}/cloudbeaver-ce-${CLOUDBEAVER_VERSION}-linux.amd64.tar.gz \
    && tar -xzf cloudbeaver-ce-${CLOUDBEAVER_VERSION}-linux.amd64.tar.gz --strip-components=1 \
    && rm cloudbeaver-ce-${CLOUDBEAVER_VERSION}-linux.amd64.tar.gz \
    && chmod +x run-server.sh

EXPOSE 8978

CMD ["./run-server.sh"]
