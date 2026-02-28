## Challenge Tasks

### Task 1: Install & Verify
1. Check if Docker Compose is available on your machine
```bash
docker-compose --version
```
2. Verify the version

---

### Task 2: Your First Compose File
1. Create a folder `compose-basics`
```bash
mkdir compose-basics
cd compose-basics
```
2. Write a `docker-compose.yml` that runs a single **Nginx** container with port mapping
```yaml
services:
  web:
    image: nginx:latest
    container_name: my-nginx
    ports:
      - "8080:80"
```
3. Start it with `docker compose up`
```bash
docker compose up
```
4. Access it in your browser
- http://<your-public-ip>:8080
5. Stop it with `docker compose down`
```bash
docker compose down
```
---

### Task 3: Two-Container Setup
Write a `docker-compose.yml` that runs:
- A **WordPress** container
- A **MySQL** container

They should:
- Be on the same network (Compose does this automatically)
- MySQL should have a named volume for data persistence
- WordPress should connect to MySQL using the service name

Start it, access WordPress in your browser, and set it up.

**Verify:** Stop and restart with `docker compose down` and `docker compose up` — is your WordPress data still there?

```bash
mkdir wordpress-compose
cd wordpress-compose
vi docker-compose.yml
```

```YAML
version: "3.9"

services:
  db:
    image: mysql:8.0
    container_name: wp-mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wpuser
      MYSQL_PASSWORD: wppass
    volumes:
      - db_data:/var/lib/mysql

  wordpress:
    image: wordpress:latest
    container_name: wp-app
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wpuser
      WORDPRESS_DB_PASSWORD: wppass
      WORDPRESS_DB_NAME: wordpress
    depends_on:
      - db

volumes:
  db_data:
```

```bash
docker compose up -d
docker ps
```

- is your WordPress data still there : YES

---

### Task 4: Compose Commands
Practice and document these:
1. Start services in **detached mode**
```bash
docker compose up -d
```
2. View running services
```bash
docker compose ps
```
3. View **logs** of all services
```bash
docker compose logs
```
4. View logs of a **specific** service
```bash
docker compose logs wordpress
docker compose logs -f wordpress
```
5. **Stop** services without removing
```bash
docker compose stop
```
6. **Remove** everything (containers, networks)
```bash
docker compose down
```
7. **Rebuild** images if you make a change
```bash
docker compose up -d --build

OR

docker compose build
docker compose up -d
```

| Action              | Command                            |
| ------------------- | ---------------------------------- |
| Start (background)  | `docker compose up -d`             |
| View services       | `docker compose ps`                |
| View all logs       | `docker compose logs`              |
| View specific logs  | `docker compose logs service-name` |
| Stop only           | `docker compose stop`              |
| Remove containers   | `docker compose down`              |
| Remove with volumes | `docker compose down -v`           |
| Rebuild             | `docker compose up -d --build`     |


---

### Task 5: Environment Variables
1. Add environment variables directly in your `docker-compose.yml`
```YAML
version: "3.9"

services:
  app:
    image: nginx
    container_name: env-test
    ports:
      - "8080:80"
    environment:
      APP_ENV: development
      APP_DEBUG: "true"
```
```bash
docker compose up -d
docker exec -it env-test bash
env
```

2. Create a `.env` file and reference variables from it in your compose file
```bash
vim .env
```

```code
APP_ENV=production
APP_DEBUG=false
```

```YAML
version: "3.9"

services:
  app:
    image: nginx
    container_name: env-test
    ports:
      - "8080:80"
    environment:
      APP_ENV: ${APP_ENV}
      APP_DEBUG: ${APP_DEBUG}
```

```bash
docker compose up -d
```

3. Verify the variables are being picked up

```bash
docker exec -it env-test bash
env
```

- Values are taken from .env file.