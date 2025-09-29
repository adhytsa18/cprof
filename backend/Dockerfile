FROM python:3.13-slim

# 1️⃣ Install dependency build untuk mysqlclient
RUN apt-get update && apt-get install -y \
    build-essential \
    pkg-config \
    default-libmysqlclient-dev \
    && rm -rf /var/lib/apt/lists/*

# 2️⃣ Copy requirements
WORKDIR /app
COPY requirements.txt .

# 3️⃣ Install Python packages
RUN pip install --no-cache-dir -r requirements.txt

# 4️⃣ Copy project
COPY . .

CMD ["gunicorn", "cprof.wsgi:application", "--bind", "0.0.0.0:8000"]
