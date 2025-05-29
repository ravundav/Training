# Docker commands with Explanations

## 1. Docker Basics

| Command | Description |
|---------|-------------|
| `docker --version` | Show Docker version installed. |
| `docker info` | Display system-wide information about Docker. |
| `docker help` | List all Docker commands or get help for a specific command. |


## 2. Images

| Command | Description |
|---------|-------------|
| `docker pull <image>` | Download an image from Docker Hub (e.g., `docker pull nginx`). |
| `docker images` | List all images on your local machine. |
| `docker rmi <image>` | Remove an image by name or ID. |
| `docker build -t <name>:<tag> .` | Build an image from a Dockerfile in the current directory. |

## 3. Containers

| Command | Description |
|---------|-------------|
| `docker run <image>` | Run a container from an image (default foreground mode). |
| `docker run -d <image>` | Run a container in detached (background) mode. |
| `docker run -it <image> /bin/bash` | Run interactively with a shell. |
| `docker ps` | List running containers. |
| `docker ps -a` | List all containers (including stopped). |
| `docker stop <container>` | Stop a running container. |
| `docker start <container>` | Start a stopped container. |
| `docker restart <container>` | Restart a container. |
| `docker rm <container>` | Remove a container. |
| `docker exec -it <container> /bin/bash` | Run a command inside a running container. |

## 4. Volumes & Data

| Command | Description |
|---------|-------------|
| `docker volume create <name>` | Create a named volume. |
| `docker volume ls` | List all volumes. |
| `docker run -v <volume>:/path/in/container <image>` | Mount a volume into a container. |
| `docker run -v $(pwd):/app <image>` | Mount current directory into container. |

## 5. Networking

| Command | Description |
|---------|-------------|
| `docker network ls` | List all networks. |
| `docker network create <name>` | Create a new network. |
| `docker run --network=<name> <image>` | Connect a container to a network. |
| `docker run -p 8080:80 <image>` | Map host port 8080 to container port 80. |

## 6. Docker Compose

| Command | Description |
|---------|-------------|
| `docker-compose up` | Start services defined in `docker-compose.yml`. |
| `docker-compose up -d` | Start services in detached mode. |
| `docker-compose down` | Stop and remove containers, networks, volumes. |
| `docker-compose build` | Build or rebuild services. |

## 7. Dockerfile Essentials

| Instruction | Description |
|-------------|-------------|
| `FROM` | Base image to use. |
| `COPY` | Copy files from host to image. |
| `RUN` | Run a command during build. |
| `CMD` | Default command to run in container. |
| `EXPOSE` | Document the port the container listens on. |
| `ENV` | Set environment variables. |
| `WORKDIR` | Set working directory inside container. |

## 8. Cleanup

| Command | Description |
|---------|-------------|
| `docker system prune` | Remove unused data (containers, images, networks). |
| `docker image prune` | Remove unused images. |
| `docker container prune` | Remove stopped containers. |
| `docker volume prune` | Remove unused volumes. |

---

**Tip:**  
Use `docker <command> --help` for more details on any command.
