# Docker Setup for Nuxt 3 Project

This project includes Docker configurations for both development and production environments using `Dockerfile`, `Dockerfile.dev`, `docker-compose.yml`, and `docker-compose.dev.yml`.

## Prerequisites

Ensure you have the following installed:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [OrbStack](https://orbstack.dev/) (optional, as a supercharged alternative to Docker Desktop and WSL)

---

## Development Setup

For local development, use `docker-compose.dev.yml` to set up the environment with hot reload enabled.

### Run Development Environment

```bash
docker compose -f docker-compose.dev.yml up --build
```

### Explanation:

- `-f docker-compose.dev.yml` - Specifies the development Docker Compose file.
- `--build` - Ensures the image is rebuilt with the latest changes.

### Development Features:

- **Hot Reloading** – Changes to source files will automatically reflect inside the container.
- **Mounted Volumes** – Your local files are synced with the container.
- **Port Forwarding** – Access the app at `http://localhost:3000`.

---

## Production Setup

For production, use the standard `docker-compose.yml` with an optimized build for deployment.

### Build and Run Production Container

```bash
docker compose up --build -d
```

### Explanation:

- `up` - Starts the production container.
- `--build` - Builds the production image.
- `-d` - Runs the container in detached mode.

### Production Features:

- **Optimized Image** – Smaller and more efficient build.
- **No Development Dependencies** – Only necessary files are included.
- **Environment Variables** – Configurable via `.env` file.

---

## File Structure Overview

- **Dockerfile** - Production build setup.
- **Dockerfile.dev** - Development setup with hot reloading.
- **docker-compose.yml** - Production service definitions.
- **docker-compose.dev.yml** - Development service definitions.
- **.dockerignore** - Excludes unnecessary files from being copied into the container.

---

## Stopping Containers

To stop the running containers:

```bash
docker compose down
```

For the development environment:

```bash
docker compose -f docker-compose.dev.yml down
```

---

## Cleaning Up

To remove all containers and volumes:

```bash
docker compose down --volumes
```

To remove unused images:

```bash
docker image prune -a
```

---

## Troubleshooting

### Common Issues and Solutions

1. **File changes not triggering hot reload**
   - Ensure `CHOKIDAR_USEPOLLING=true` is set in your `docker-compose.dev.yml`.

2. **Port already in use errors**
   - Run `docker ps` to check for running containers and stop conflicting ones.

3. **Permission issues with mounted volumes**
   - Ensure the correct file permissions are set on your local system.

---

## Additional Resources

For further reading and best practices, check out the following resources:

1. [Running Nuxt 3 in a Docker Container](https://markus.oberlehner.net/blog/running-nuxt-3-in-a-docker-container/)
2. [Dockerizing a Nuxt App](https://mokkapps.de/blog/dockerizing-a-nuxt-app)
3. [OrbStack - A Faster Alternative to Docker Desktop](https://orbstack.dev/)

For any additional questions, refer to the official [Docker documentation](https://docs.docker.com/).
