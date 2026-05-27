## Deployment Workflow

This project uses a Docker-based CI/CD deployment workflow with GitHub Actions, Docker Hub, and AWS EC2.

### Deployment Process

1. Code is pushed to the `main` branch on GitHub.
2. GitHub Actions automatically:

   * Checks out the latest code
   * Builds a Docker image
   * Pushes the image to Docker Hub
3. GitHub Actions connects to the EC2 server via SSH.
4. The EC2 server:

   * Pulls the latest repository changes using `git pull`
   * Pulls the latest Docker image from Docker Hub
   * Restarts containers using Docker Compose

### EC2 Server Setup

The EC2 instance contains:

* Docker
* Docker Compose
* Git
* Full project repository
* `docker-compose.yml`
* Environment configuration files

### Deployment Commands Executed on EC2

```bash
git pull origin main
docker compose pull
docker compose up -d
```

### Benefits of This Approach

* Automated deployments using GitHub Actions
* Consistent containerized environment
* Latest configuration and deployment files automatically synced from GitHub
* Simple and production-friendly setup for small to mid-sized applications
