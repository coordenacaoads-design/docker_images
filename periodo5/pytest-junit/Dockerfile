# PyTest / JUnit - 5o Periodo
FROM eclipse-temurin:21-jdk-jammy

LABEL description="PyTest (Python) + JUnit (Java) para testes automatizados"

ENV JUNIT_VERSION=1.11.2

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip wget maven \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir --break-system-packages pytest pytest-cov

RUN mkdir -p /opt/junit \
    && wget -q -O /opt/junit/junit-platform-console-standalone.jar \
    https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/${JUNIT_VERSION}/junit-platform-console-standalone-${JUNIT_VERSION}.jar

WORKDIR /workspace
CMD ["bash"]
