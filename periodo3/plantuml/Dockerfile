# PlantUML - 3o Periodo
FROM eclipse-temurin:21-jre-jammy

LABEL description="PlantUML (gera diagramas a partir de texto)"

RUN apt-get update && apt-get install -y --no-install-recommends \
    graphviz \
    wget \
    && rm -rf /var/lib/apt/lists/* \
    && wget -q -O /opt/plantuml.jar https://github.com/plantuml/plantuml/releases/latest/download/plantuml.jar

WORKDIR /workspace

ENTRYPOINT ["java", "-jar", "/opt/plantuml.jar"]
CMD ["-version"]
