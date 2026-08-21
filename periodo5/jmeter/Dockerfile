# Apache JMeter - 5o Periodo
FROM eclipse-temurin:17-jdk-jammy

LABEL description="Apache JMeter"

ENV JMETER_VERSION=5.6.3 \
    JMETER_HOME=/opt/apache-jmeter

RUN apt-get update && apt-get install -y --no-install-recommends wget \
    && wget -q https://dlcdn.apache.org/jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz \
    && tar -xzf apache-jmeter-${JMETER_VERSION}.tgz -C /opt \
    && mv /opt/apache-jmeter-${JMETER_VERSION} ${JMETER_HOME} \
    && rm apache-jmeter-${JMETER_VERSION}.tgz \
    && apt-get purge -y wget && rm -rf /var/lib/apt/lists/*

ENV PATH="${JMETER_HOME}/bin:${PATH}"

WORKDIR /workspace
ENTRYPOINT ["jmeter"]
CMD ["--version"]
