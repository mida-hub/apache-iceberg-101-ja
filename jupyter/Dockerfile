FROM python:3.11-slim

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN pip install uv

WORKDIR /home/iceberg

COPY requirements.txt .
RUN uv pip install --system -r requirements.txt

RUN mkdir -p /home/iceberg/notebooks /home/iceberg/warehouse

EXPOSE 8888

CMD ["jupyter", "lab", \
     "--notebook-dir=/home/iceberg/notebooks", \
     "--ip=0.0.0.0", \
     "--port=8888", \
     "--no-browser", \
     "--allow-root", \
     "--NotebookApp.token=", \
     "--NotebookApp.password="]
