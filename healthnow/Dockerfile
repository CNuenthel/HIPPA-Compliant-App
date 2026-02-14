FROM python:3.12.9-bookworm

RUN apt-get update && \
    apt-get upgrade -y && \
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

COPY app/app.py /app/app.py
COPY app/static /app/static
COPY app/flag.txt /app/flag.txt

RUN groupadd -g 1000 ubuntu && \
    useradd ubuntu -u 1000 -g 1000 -m -s /bin/bash && \
    chown -R root:root /app/ && \
    mkdir -p /app/data && \
    chown ubuntu:ubuntu /app/data

EXPOSE 8000

USER ubuntu
WORKDIR /app

CMD ["python3", "/app/app.py"]