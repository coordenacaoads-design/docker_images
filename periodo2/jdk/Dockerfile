# JDK (Java Development Kit) - 2o e 4o Periodo
FROM eclipse-temurin:21-jdk-jammy

LABEL description="JDK + Maven + Gradle"

RUN apt-get update && apt-get install -y --no-install-recommends \
    maven \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*

ENV GRADLE_VERSION=8.10 \
    GRADLE_HOME=/opt/gradle

RUN wget -q https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
    && unzip -q gradle-${GRADLE_VERSION}-bin.zip -d /opt \
    && mv /opt/gradle-${GRADLE_VERSION} ${GRADLE_HOME} \
    && rm gradle-${GRADLE_VERSION}-bin.zip

ENV PATH="${GRADLE_HOME}/bin:${PATH}"

WORKDIR /workspace
CMD ["bash"]
