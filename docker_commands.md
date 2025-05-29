# Docker commands with Explanations

## 1. Docker Basics

| Command | Description |
|---------|-------------|
| `docker --version` | Show Docker version installed. |
| `docker info` | Display system-wide information about Docker. |
| `docker help` | List all Docker commands or get help for a specific command. |


```
Jenkins-Docker # docker --version
Docker version 28.1.1, build 4eba37

Jenkins-Docker # docker info
Client: Docker Engine - Community
 Version:    28.1.1
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.23.0
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.35.1
    Path:     /usr/libexec/docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 1
 Server Version: 28.1.1
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: systemd
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 05044ec0a9a75232cad458027ca83437aae3f4da
 runc version: v1.2.5-0-g59923ef
 init version: de40ad0
 Security Options:
  apparmor
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.8.0-1029-aws
 Operating System: Ubuntu 24.04.2 LTS
 OSType: linux
 Architecture: x86_64
 CPUs: 2
 Total Memory: 3.82GiB
 Name: ip-172-31-85-191
 ID: 16f36410-7659-4fce-b5a3-5072221a41d3
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false

Jenkins-Docker # docker help
Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  bake        Build from a file
  pull        Download an image from a registry
  push        Upload an image to a registry
  images      List images
  login       Authenticate to a registry
  logout      Log out from a registry
```

## 2. Images

| Command | Description |
|---------|-------------|
| `docker pull <image>` | Download an image from Docker Hub (e.g., `docker pull nginx`). |
| `docker images` | List all images on your local machine. |
| `docker rmi <image>` | Remove an image by name or ID. |
| `docker build -t <name>:<tag> .` | Build an image from a Dockerfile in the current directory. |

```
Jenkins-Docker # docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE


Jenkins-Docker # docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
0622fac788ed: Pull complete
Digest: sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505d2233
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

Jenkins-Docker # docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
ubuntu       latest    a0e45e2ce6e6   4 weeks ago   78.1MB

Jenkins-Docker # docker rmi a0e45e2ce6e6
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505d2233
Deleted: sha256:a0e45e2ce6e6e22e73185397d162a64fcf2f80a41c597015cab05d9a7b5913ce
Deleted: sha256:8901a649dd5a9284fa6206a08f3ba3b5a12fddbfd2f82c880e68cdb699d98bfb

Jenkins-Docker # docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
Jenkins-Docker #
Jenkins-Docker #
```
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

```
Jenkins-Docker # docker run ubuntu
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
0622fac788ed: Pull complete
Digest: sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505d2233
Status: Downloaded newer image for ubuntu:latest

Jenkins-Docker # docker run -d ubuntu
22a784396505a797129cfe70d4bd030529b70c09f3c3b831ad6e81905f0345d0

Jenkins-Docker # docker run -it ubuntu /bin/bash
root@c81a5f07b9d4:/#
root@c81a5f07b9d4:/# exit

Jenkins-Docker # docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

Jenkins-Docker # docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                        PORTS     NAMES
c81a5f07b9d4   ubuntu    "/bin/bash"   22 seconds ago   Exited (127) 10 seconds ago             hopeful_panini
22a784396505   ubuntu    "/bin/bash"   41 seconds ago   Exited (0) 40 seconds ago               pensive_turing
641ab1bc4bd6   ubuntu    "/bin/bash"   57 seconds ago   Exited (0) 56 seconds ago               nervous_buck

Jenkins-Docker # docker stop c81a5f07b9d4
c81a5f07b9d4

Jenkins-Docker # docker start c81a5f07b9d4
c81a5f07b9d4

Jenkins-Docker #
Jenkins-Docker # docker restart c81a5f07b9d4
c81a5f07b9d4

Jenkins-Docker # docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED              STATUS          PORTS     NAMES
c81a5f07b9d4   ubuntu    "/bin/bash"   About a minute ago   Up 33 seconds             hopeful_panini

Jenkins-Docker # docker stop c81a5f07b9d4
c81a5f07b9d4
Jenkins-Docker # docker rm c81a5f07b9d4
c81a5f07b9d4
```

## 4. Volumes & Data

| Command | Description |
|---------|-------------|
| `docker volume create <name>` | Create a named volume. |
| `docker volume ls` | List all volumes. |
| `docker run -v <volume>:/path/in/container <image>` | Mount a volume into a container. |
| `docker run -v $(pwd):/app <image>` | Mount current directory into container. |

```
Jenkins-Docker # docker volume ls
DRIVER    VOLUME NAME

Jenkins-Docker # docker volume create training
training

Jenkins-Docker # docker volume ls
DRIVER    VOLUME NAME
local     training

Jenkins-Docker # docker run -v training:/training ubuntu /bin/bash
Jenkins-Docker #

Jenkins-Docker # cd
Jenkins-Docker # ls
distros  snap  source

Jenkins-Docker # docker run -it -v $(pwd):/app ubuntu /bin/bash
root@897dc0b766a6:/# ls /app
distros  snap  source
root@897dc0b766a6:/#

Jenkins-Docker # docker ps -aq
897dc0b766a6
69086878419a
eb38bbff7bf3
67ba376a1bca

Jenkins-Docker # docker rm `docker ps -aq`
897dc0b766a6
69086878419a
eb38bbff7bf3
67ba376a1bca

Jenkins-Docker # docker ps -aq
Jenkins-Docker #
```
## 5. Networking

| Command | Description |
|---------|-------------|
| `docker network ls` | List all networks. |
| `docker network create <name>` | Create a new network. |
| `docker run --network=<name> <image>` | Connect a container to a network. |
| `docker run -p 8080:80 <image>` | Map host port 8080 to container port 80. |

```
Jenkins-Docker # docker network create training
6d30a308867ff81c1546f2fd8bbae363cbbcedfd6e51587a110c83a972c2d57d

Jenkins-Docker # docker network ls
NETWORK ID     NAME       DRIVER    SCOPE
00bc9c99beef   bridge     bridge    local
c93f1aa643fa   host       host      local
43c9a5835c9c   none       null      local
6d30a308867f   training   bridge    local

Jenkins-Docker # docker run --network=training ubuntu

Jenkins-Docker # docker run -p 8080:80 ubuntu
```
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

```
Jenkins-Docker # docker system prune
WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all dangling images
  - unused build cache

Are you sure you want to continue? [y/N] y
Deleted Containers:
6f199e951538b4bab1ec6016d3d251a3cc6fd337c6adefbf5d3538429182e7ca
ae6808dcae50aa40f88cffb173a0ccda001078bfd4457df4ab19e00424d8707a

Deleted Networks:
training

Total reclaimed space: 0B
Jenkins-Docker # docker image prune
WARNING! This will remove all dangling images.
Are you sure you want to continue? [y/N] y
Total reclaimed space: 0B


Jenkins-Docker # docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Total reclaimed space: 0B

Jenkins-Docker # docker volume prune
WARNING! This will remove anonymous local volumes not used by at least one container.
Are you sure you want to continue? [y/N] y
Total reclaimed space: 0B
Jenkins-Docker #
```
---

**Tip:**  
Use `docker <command> --help` for more details on any command.
