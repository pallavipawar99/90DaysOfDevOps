## Quick-Fire Questions

1. What is the difference between an image and a container?

- Image = Blueprint / template (read-only).
It contains the app code, libraries, dependencies, and configuration.
- Container = Running instance of an image.
It is a live, isolated environment created from an image.
- Image is like a class, container is like an object (instance).

2. What happens to data inside a container when you remove it?

- All data stored inside the container’s writable layer is deleted.
- Data is preserved only if:
    - You used a named volume, or
    - You used a bind mount.
- No volume = data loss after docker rm.

3. How do two containers on the same custom network communicate?

- They can communicate using container names as hostnames.
```bash
docker network create mynet
docker run --network mynet --name app ...
docker run --network mynet --name db ...
```

4. What does `docker compose down -v` do differently from `docker compose down`?

- docker compose down
    - Stops containers
    - Removes containers
    - Removes networks

- docker compose down -v
    - Does everything above
    - Also removes named volumes

- -v deletes persistent data.

5. Why are multi-stage builds useful?

- Reduce final image size
- Remove build tools from production image
- Improve security
- Make images cleaner and faster

6. What is the difference between `COPY` and `ADD`?



7. What does `-p 8080:80` mean?

- Port 8080 on your host machine
- Is mapped to port 80 inside the container

8. How do you check how much disk space Docker is using?

- docker system df
- docker system df -v ( To see detailed info)