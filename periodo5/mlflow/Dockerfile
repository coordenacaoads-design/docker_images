# MLflow - 5o Periodo
FROM python:3.12-slim

LABEL description="MLflow tracking server"

RUN pip install --no-cache-dir mlflow

EXPOSE 5000

CMD ["mlflow", "server", "--host", "0.0.0.0", "--port", "5000"]
