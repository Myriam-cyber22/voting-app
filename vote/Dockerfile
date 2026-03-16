FROM python:3.11.15-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt && \
    apt-get update && apt-get install -y curl && \
    rm -rf /var/lib/apt/lists/*

COPY . .

EXPOSE 8080

HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
    CMD curl -f http://localhost:8080 || exit 1

CMD ["python", "app.py"]