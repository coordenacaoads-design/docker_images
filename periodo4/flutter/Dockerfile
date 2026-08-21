# Flutter SDK - 4o Periodo
FROM ubuntu:22.04

LABEL description="Flutter SDK (canal stable)"

ENV DEBIAN_FRONTEND=noninteractive \
    FLUTTER_HOME=/opt/flutter \
    PATH="/opt/flutter/bin:${PATH}"

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl git unzip xz-utils zip libglu1-mesa ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 --branch stable https://github.com/flutter/flutter.git ${FLUTTER_HOME}

RUN flutter precache && flutter doctor

WORKDIR /workspace
CMD ["bash"]
