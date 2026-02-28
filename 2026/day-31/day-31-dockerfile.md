# Day 31 – Dockerfile: Build Your Own Images

## Challenge Tasks

### Task 1: Your First Dockerfile
1. Create a folder called `my-first-image`
```bash
mkdir my-first-image
cd my-first-image
```
2. Inside it, create a `Dockerfile` that:
   - Uses `ubuntu` as the base image
   - Installs `curl`
   - Sets a default command to print `"Hello from my custom image!"`
```dockerfile
FROM ubuntu:latest

RUN apt-get update && apt-get install -y curl

CMD ["echo", "Hello from my custom image!"]
```
3. Build the image and tag it `my-ubuntu:v1`
```bash
docker build -t my-ubuntu:v1 .
```
4. Run a container from your image
```bash
docker run my-ubuntu:v1
```

---

### Task 2: Dockerfile Instructions
Create a new Dockerfile that uses **all** of these instructions:
- `FROM` — base image
- `RUN` — execute commands during build
- `COPY` — copy files from host to image
- `WORKDIR` — set working directory
- `EXPOSE` — document the port
- `CMD` — default command
```dockerfile
FROM ubuntu:latest

RUN apt-get update && apt-get install -y curl

WORKDIR /app

COPY app.txt .

EXPOSE 8080

CMD ["cat", "app.txt"]
```

| Instruction | Purpose                         |
| ----------- | ------------------------------- |
| FROM        | Base image                      |
| RUN         | Execute commands during build   |
| WORKDIR     | Sets working directory          |
| COPY        | Copies files from host to image |
| EXPOSE      | Documents port                  |
| CMD         | Default container command       |

---

### Task 3: CMD vs ENTRYPOINT
1. Create an image with `CMD ["echo", "hello"]` — run it, then run it with a custom command. What happens?
```dockerfile
FROM ubuntu
CMD ["echo", "hello"]
```
```bash
docker build -t cmd-image .   
docker run cmd-image  ==> hello

docker run cmd-image echo world  ==> world
```
- CMD can be overridden completely.
- If you provide another command, it replaces CMD.

2. Create an image with `ENTRYPOINT ["echo"]` — run it, then run it with additional arguments. What happens?
```dockerfile
FROM ubuntu
ENTRYPOINT ["echo"]
```
```bash
docker run entry-image hello ==> hello
docker run entry-image world ==> world
```
- ENTRYPOINT is fixed.
- Extra arguments are appended to ENTRYPOINT.
- You cannot override it easily.

3. Write in your notes: When would you use CMD vs ENTRYPOINT?
### 1. Use `CMD` when:
* You want to provide a **default** shell or application.
* You want to allow users to easily run different commands without extra flags.
* **Example:** `CMD ["python", "main.py"]` (If the user runs `docker run image bash`, it ignores the python script entirely).

### 2. Use `ENTRYPOINT` when:
* You want the container to behave like a **specific tool** (e.g., a database or a CLI tool).
* You want to ensure the main process is never accidentally skipped.
* **Example:** `ENTRYPOINT ["git"]` (The container now acts exactly like the git command).

---

### Task 4: Build a Simple Web App Image
1. Create a small static HTML file (`index.html`) with any content

2. Write a Dockerfile that:
   - Uses `nginx:alpine` as base
   - Copies your `index.html` to the Nginx web directory
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```
3. Build and tag it `my-website:v1`
```bash
docker build -t my-website:v1 .
```
4. Run it with port mapping and access it in your browser
```bash
docker run -d -p 80:80 my-website:v1
```
---

### Task 5: .dockerignore
1. Create a `.dockerignore` file in one of your project folders
2. Add entries for: `node_modules`, `.git`, `*.md`, `.env`
```code 
node_modules
.git
*.md
.env
```
3. Build the image — verify that ignored files are not included
```bash
docker build -t ignore-test .
```

---

### Task 6: Build Optimization
1. Build an image, then change one line and rebuild — notice how Docker uses **cache**
2. Reorder your Dockerfile so that frequently changing lines come **last**
3. Write in your notes: Why does layer order matter for build speed?
- Each Dockerfile instruction creates a layer
- Docker reuses cached layers if nothing changes
- If one layer changes, all layers after it must rebuild
- Therefore:
    - Frequently changing instructions should be placed at the bottom
    - Rarely changing instructions (like installing dependencies) should be placed at the top
