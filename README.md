# Docker
Docker Study



unzip "/workspaces/Docker/Ex_Files_Learning_Docker_2025 (2).zip"


To automatically overwrite all files without being prompted, use the -o (overwrite) flag:

unzip -o "/workspaces/Docker/Ex_Files_Learning_Docker_2025 (2).zip"


$ cd "/workspaces/Docker/Ex_Files_Learning_Docker_2025/Exercise Files/04_03_before"

ls - list





3. Running Docker in Codespaces

Problem: By default, GitHub Codespaces doesn’t give you Docker daemon access (because it’s a container itself).

✅ Workaround:

Use Docker-in-Docker setup with docker preinstalled Codespaces images, OR

Use Play with Docker (free: https://labs.play-with-docker.com/
) for practicing real Docker commands, OR

Use Docker Desktop on your machine (if performance allows), OR

Use a cloud dev environment (like ACG, Katacoda, or Docker Playground).

So in Codespaces, you can practice commands like cd, ls, editing Dockerfiles, writing YAML, but to actually run containers (docker run, docker build) you’ll need Play with Docker or a machine with Docker engine.

## Workflow: Using Docker Desktop with GitHub Codespaces

# Edit Code in Codespaces:

Use Codespaces for editing your code, Dockerfiles, and configuration files.
Commit and push your changes to GitHub.


# Clone Repo Locally:

On your local machine (with Docker Desktop installed), clone your GitHub repository:

```
git clone <your-repo-url>
cd <your-repo>
```
# Build and Run with Docker Desktop:

Use Docker Desktop to build and run your containers locally:
```
docker build -t my-image .
docker run -p 8080:80 my-image
```
# Sync Changes:

Make changes in Codespaces, push to GitHub, then pull updates on your local machine to test with Docker Desktop.


