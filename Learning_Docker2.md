# Learning Docker - Hands-on Experience

This document contains my hands-on experience with Docker, including commands I've executed and their explanations.

## Initial Setup and Exploration

### Cloning Docker Repository
```bash
git clone https://github.com/buvir/Docker
```
This command clones a Docker repository from GitHub to my local machine, which contains various Docker learning resources.

### Navigating to Docker Directory
```bash
cd Docker
```
Changes the current working directory to the Docker folder that was just cloned.

### Listing Directory Contents
```bash
ls
```
Lists all files and directories in the current Docker folder, showing:

- Ex_Files_Learning_Docker_2025 (directory)
- Docker_cheatsheet.md
- Docker_notes.md
- Docker_Study.ipynb
- README.md

## Basic Docker Commands

### Checking Running Containers
```bash
docker ps
```
Lists all currently running Docker containers. The output shows multiple containers running, mostly related to Kubernetes which is integrated with Docker Desktop.

### Running Hello World Container
```bash
docker run hello-world
```
This command:

- Checks locally for the 'hello-world' image
- When not found locally, pulls it from Docker Hub
- Creates a new container from the image
- Executes the container which displays the welcome message

Output shows:
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete
Digest: sha256:a0dfb02aac212703bfcb339d77d47ec32c8706ff250850ecc0e19c8737b18567
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

### Getting Docker Help
```bash
docker --help
```
Displays all available Docker commands and options, organized into:

- Common Commands (run, exec, ps, build, etc.)
- Management Commands (container, image, network, etc.)
- Swarm Commands
- Global Options

### Exploring Network Commands
```bash
docker network --help
```
Shows available Docker network management commands (connect, create, disconnect, inspect, ls, prune, rm).

### Exploring Container Creation
```bash
docker container create --help
```
Displays extensive help for the docker container create command, showing all available options for creating containers.

## Working with Containers

### Creating a Container from Image
```bash
docker container create hello-world
```
Creates a container from the hello-world image but doesn't start it. Returns a container ID:
```
95ce64277392aa46f0dc125d05cd52d748de89638715fcbc7b3ece125f76ac73
```

### Creating Container with Specific Tag
```bash
docker container create hello-world:linux
```
Creates a container from the hello-world:linux image (pulls it first if not available locally).

### Viewing All Containers
```bash
docker ps --all
```
Shows all containers, both running and stopped, including:

- The hello-world containers we created
- Various Kubernetes system containers
- Previous containers from months ago

### Starting a Container
```bash
docker container start 1e9d11d04fb3255de2f39801ff714da93ed84fe80eb953a5d0487012646ce243
```
Starts the previously created container (using its ID).

### Viewing Container Logs
```bash
docker logs 1e9
```
Displays the output from the hello-world container (using shortened container ID).

### Starting Container with Attach Mode
```bash
docker container start --attach 1e9
```
Starts the container and attaches the terminal to it, showing the output directly.

### Running Latest Linux Hello-World
```bash
docker run hello-world:linux
```
Runs the hello-world:linux image directly (pull+create+start+output).

## Working with Dockerfiles and Building Images

### Attempting to Use Text Editors
```bash
vim Dockerfile
```
Attempted to use vim editor (not available on Windows by default).

```bash
notepad Dockerfile
```
Successfully opened Dockerfile in Notepad editor.

### Building a Docker Image
```bash
docker build -t our-first-image .
```
Builds a Docker image from the Dockerfile in the current directory and tags it as "our-first-image". The build process shows each step:

- Loads build definition from Dockerfile
- Loads metadata for Ubuntu base image
- Transfers build context
- Executes each instruction in the Dockerfile
- Exports the final image

### Using Buildx for Building
```bash
docker buildx build -t our-first-image .
```
Uses BuildKit (extended build capabilities) to build the image, which is faster due to caching.

### Running the Custom Image
```bash
docker run --rm our-first-image
```
Runs a container from our custom image and removes it after execution. Output shows:
```
Hello! The current date and time is Tue, 09 Sep 2025 12:17:12 GMT
```

## Working with Multiple Dockerfiles

### Building from a Specific Dockerfile
```bash
docker build --file server.Dockerfile --tag our-first-server .
```
Builds an image using a specific Dockerfile (server.Dockerfile) instead of the default Dockerfile.

### Running a Server Container
```bash
docker run our-first-server
```
Runs a server container that stays running until stopped with CTRL-C.

### Running in Detached Mode
```bash
docker run -d our-first-server
```
Runs the container in detached mode (background).

## Executing Commands in Running Containers

```bash
docker exec af9 date
```
Executes the date command inside the running container.

```bash
docker exec --interactive --tty af99 bash
```
Opens an interactive bash shell inside the running container.

## Stopping Containers

```bash
docker stop af9
```
Gracefully stops a running container.

```bash
docker stop -t 0 e6a
```
Stops a container immediately (without waiting for graceful shutdown).

## Container Management

### Viewing All Containers
```bash
docker ps -a
```
Shows all containers (both running and stopped).

### Removing Containers
```bash
docker rm e6a
```
Removes a stopped container.

### Force Removing Multiple Containers
```bash
docker ps -aq | ForEach-Object { docker rm -f $_ }
```
Uses PowerShell to force remove all containers (running and stopped).

### Removing Images
```bash
docker rmi our-first-server
```
Removes the specified Docker image.

## Key Concepts Demonstrated

- **Images vs Containers**: Images are templates, containers are running instances
- **Container Lifecycle**: create → start → stop → remove
- **Logs**: Viewing container output after execution
- **Tags**: Using specific image versions with tags like `:linux`
- **Dockerfiles**: Building custom images from instructions
- **Build Cache**: Faster builds using cached layers
- **Interactive vs Detached**: Different ways to run containers
- **Executing Commands**: Running commands inside containers
- **Help System**: Exploring available commands and options

This hands-on experience demonstrates fundamental Docker operations that form the foundation for container management and deployment.
