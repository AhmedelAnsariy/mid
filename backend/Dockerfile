# Stage 1: Install dependencies
FROM python:3.10-slim as builder

WORKDIR /app

COPY requirements.txt .
RUN pip install --upgrade pip
RUN pip install --user -r requirements.txt

# Stage 2: Final image
FROM python:3.10-slim

WORKDIR /app

COPY --from=builder /root/.local /root/.local
ENV PATH=/root/.local/bin:$PATH

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
