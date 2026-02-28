## Challenge Tasks

### Task 1: Build Your Own App Stack
Create a `docker-compose.yml` for a 3-service stack:
- A **web app** (use Python Flask, Node.js, or any language you know)
- A **database** (Postgres or MySQL)
- A **cache** (Redis)

Write a simple Dockerfile for the web app. The app doesn't need to be complex — even a "Hello World" that connects to the database is enough.

```bash
app-stack/
│
├── docker-compose.yml
├── app/
│   ├── Dockerfile
│   ├── requirements.txt
│   └── app.py

mkdir app-stack
cd app-stack
mkdir app

```

- app/app.py

```python
from flask import Flask
import psycopg2
import redis
import os

app = Flask(__name__)

DB_HOST = os.getenv("DB_HOST")
DB_NAME = os.getenv("POSTGRES_DB")
DB_USER = os.getenv("POSTGRES_USER")
DB_PASS = os.getenv("POSTGRES_PASSWORD")
REDIS_HOST = os.getenv("REDIS_HOST")

@app.route("/")
def hello():
    try:
        conn = psycopg2.connect(
            host=DB_HOST,
            database=DB_NAME,
            user=DB_USER,
            password=DB_PASS
        )
        conn.close()
        db_status = "Connected to Postgres ✅"
    except Exception as e:
        db_status = f"Postgres Error ❌ {e}"

    try:
        r = redis.Redis(host=REDIS_HOST, port=6379)
        r.ping()
        cache_status = "Connected to Redis ✅"
    except Exception as e:
        cache_status = f"Redis Error ❌ {e}"

    return f"Hello from Flask!<br>{db_status}<br>{cache_status}"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

- app/requirements.txt

```bash
flask
psycopg2-binary
redis
```

- app/Dockerfile

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

EXPOSE 5000

CMD ["python", "app.py"]
```

```YAML
version: "3.9"

services:

  web:
    build: ./app
    container_name: flask-app
    ports:
      - "5000:5000"
    environment:
      DB_HOST: db
      POSTGRES_DB: mydb
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      REDIS_HOST: redis
    depends_on:
      - db
      - redis

  db:
    image: postgres:15
    container_name: postgres-db
    restart: always
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
    volumes:
      - pgdata:/var/lib/postgresql/data

  redis:
    image: redis:latest
    container_name: redis-cache
    restart: always

volumes:
  pgdata:
```

```bash
docker compose up -d --build
```

---

### Task 2: depends_on & Healthchecks
1. Add `depends_on` to your compose file so the app starts **after** the database
```bash
depends_on:
  db:
    condition: service_healthy
```
2. Add a **healthcheck** on the database service
```bash
healthcheck:
  test: ["CMD-SHELL", "pg_isready -U myuser -d mydb"]
```
3. Use `depends_on` with `condition: service_healthy` so the app waits for the database to be truly ready, not just started

**Test:** Bring everything down and up — does the app wait for the DB?

```bash
docker-compose down
docker-compose up -d --build
docker-compose logs -f
docker ps
```

| Without Healthcheck    | With Healthcheck   |
| ---------------------- | ------------------ |
| App starts immediately | App waits          |
| DB may not be ready    | DB confirmed ready |
| App may crash          | Stable startup     |

---

### Task 3: Restart Policies
1. Add `restart: always` to your database service
```YAML
db:
  image: postgres:15
  container_name: postgres-db
  restart: always
  environment:
    POSTGRES_DB: mydb
    POSTGRES_USER: myuser
    POSTGRES_PASSWORD: mypassword
  volumes:
    - pgdata:/var/lib/postgresql/data
```
2. Manually kill the database container — does it come back?

```bash
docker kill postgres-db
docker ps
```

- postgres-db comes back automatically `restart: always`

3. Try `restart: on-failure` — how is it different?

```YAML
restart: on-failure
```

```bash
docker-compose down
docker-compose up -d
docker kill postgres-db
```
4. Write in your notes: When would you use each restart policy?

- restart: always
- Use for:
    - Databases
    - Production APIs
    - Critical background services

- restart: on-failure
- Use for:
    - Worker jobs
    - Batch processing
    - Retry logic services

Only restart if error occurs.

---

### Task 4: Custom Dockerfiles in Compose
1. Instead of using a pre-built image for your app, use `build:` in your compose file to build from a Dockerfile
2. Make a code change in your app
3. Rebuild and restart with one command

---

### Task 5: Named Networks & Volumes
1. Define **explicit networks** in your compose file instead of relying on the default

- Why Explicit Networks?
    - Better security
    - Better isolation
    - Clear architecture
    - Production best practice

```YAML
networks:
  frontend:
  backend:
```

2. Define **named volumes** for database data

- Why Named Volumes?
    - Persistent DB data
    - Survives container removal
    - Easier backup
    - Better than anonymous volumes

```YAML
volumes:
  postgres_data:
```

3. Add **labels** to your services for better organization

- Label = extra information attached to a container for better organization and filtering.

```YAML
services:
  app:
    image: myapp
    labels:
      com.project.name: "app-stack"
      com.project.env: "dev"
      com.project.owner: "backend-team"
```

---

### Task 6: Scaling (Bonus)
1. Try scaling your web app to 3 replicas using `docker compose up --scale`
```bash
docker compose up -d --scale app=3
```

```code
app-1
app-2
app-3
```
2. What happens? What breaks?

- Only one container can use a host port at a time.
- But port 8000 is already taken by first container.
- So scaling fails.

3. Write in your notes: Why doesn't simple scaling work with port mapping?

- Port mapping binds to host machine port
- Host port must be unique
- Multiple containers cannot share same host port

