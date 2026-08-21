# Selenium - 5o Periodo
FROM python:3.12-slim

LABEL description="Selenium (Python) + Chromium headless"

RUN apt-get update && apt-get install -y --no-install-recommends \
    chromium chromium-driver \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir selenium

ENV CHROME_BIN=/usr/bin/chromium \
    CHROMEDRIVER_PATH=/usr/bin/chromedriver

WORKDIR /workspace
CMD ["python3"]
