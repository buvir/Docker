# Docker Cheatsheet 🐳

A quick reference for common Docker commands and concepts.

---

## 🔹 Docker Basics

```bash
# Check version
docker --version

# Get help
docker help

```
🔹 Images
# List images
docker images

# Pull image from Docker Hub
docker pull <image_name>:<tag>

# Build image from Dockerfile
docker build -t <image_name>:<tag> .

# Remove an image
docker rmi <image_id>
```
🔹 Containers

# Run container (interactive)
docker run -it <image_name> /bin/bash

# Run container in background
docker run -d --name <container_name> <image_name>

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container_id>

# Start a container
docker start <container_id>

# Remove a container
docker rm <container_id>

```


🔹 Container Logs & Stats

```
# View logs
docker logs <container_id>

# Stream logs
docker logs -f <container_id>

# Show container resource usage
docker stats
```
🔹 Volumes (Persistent Data)
# Create volume
docker volume create <volume_name>

# List volumes
docker volume ls

# Run with volume
docker run -v <volume_name>:/path/in/container <image_name>

🔹 Networking

```
# List networks
docker network ls

# Create network
docker network create <network_name>

# Run container on a network
docker run --network <network_name> <image_name>
```
```
🔹 Dockerfile Essentials
```
FROM ubuntu:20.04
WORKDIR /app
COPY . /app
RUN apt-get update && apt-get install -y python3
CMD ["python3", "app.py"]


🔹 Docker Compose
```
# Start services
docker-compose up

# Start in detached mode
docker-compose up -d

# Stop services
docker-compose down
```

🔹 Common Diagram (VMs vs Containers)
```
Virtual Machine
---------------
App1 | App2 | App3
  ↑      ↑      ↑
   Guest OS (each VM has one)
   Hypervisor
   Host OS
   Hardware

Container
---------
App1 | App2 | App3
  ↑      ↑      ↑
   Container Runtime
   Host OS
   Hardware
```

✅ Key Tips

Use docker ps -a to see all containers (running + stopped).

Use tags (like nginx:latest or python:3.9) to avoid surprises.

Always clean up unused resources:
```


docker system prune
```

