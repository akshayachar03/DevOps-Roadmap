# Docker Commands (Must Know) Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is the purpose of the `docker pull` command?

**Answer**

The `docker pull` command downloads a Docker image from a container registry (such as Docker Hub) to the local machine.

Example:

```bash
docker pull nginx
```

Download a specific version:

```bash
docker pull nginx:1.27
```

**Explanation**

A Docker image must exist locally before a container can be created from it. If the image is unavailable locally, Docker can automatically pull it when running `docker run`.

**Used in Production**

- Downloading base images
- Pulling application images during deployments
- Kubernetes worker nodes pulling application images

**Common Mistake**

Assuming `docker pull` creates a running container. It only downloads the image.

---

### Question 2

**Question**

How do you view Docker images available on your system?

**Answer**

Use:

```bash
docker images
```

or

```bash
docker image ls
```

**Explanation**

This command displays:

- Repository
- Tag
- Image ID
- Creation Time
- Size

It helps verify whether the required image already exists locally.

**Used in Production**

Engineers use it before building, tagging, or removing images.

**Common Mistake**

Confusing Docker images with running containers.

---

### Question 3

**Question**

What is the purpose of the `docker build` command?

**Answer**

`docker build` creates a Docker image from a Dockerfile.

Example:

```bash
docker build -t myapp:v1 .
```

**Explanation**

Docker reads the Dockerfile instructions layer by layer and creates a reusable image.

**Used in Production**

Every CI/CD pipeline builds Docker images before deployment.

**Common Mistake**

Running `docker build` from the wrong directory where the Dockerfile is not present.

---

### Question 4

**Question**

What is the purpose of the `docker run` command?

**Answer**

`docker run` creates and starts a new container from an image.

Example:

```bash
docker run nginx
```

Run in detached mode:

```bash
docker run -d nginx
```

Expose port:

```bash
docker run -d -p 80:80 nginx
```

**Explanation**

`docker run` combines image creation and container startup in one command.

**Used in Production**

Launching application containers, databases, web servers, and microservices.

**Common Mistake**

Confusing `docker run` with `docker start`.

---

### Question 5

**Question**

What is the difference between `docker ps` and `docker ps -a`?

**Answer**

```
docker ps
```

Displays only running containers.

```
docker ps -a
```

Displays all containers including stopped ones.

**Explanation**

This helps identify whether a container is running or has exited.

**Used in Production**

Often the first command used during troubleshooting.

---

### Question 6

**Question**

What is the purpose of the `docker exec` command?

**Answer**

It executes commands inside a running container.

Example:

```bash
docker exec -it mycontainer bash
```

or

```bash
docker exec -it mycontainer sh
```

**Explanation**

It provides interactive access without restarting the container.

**Used in Production**

- Debugging applications
- Viewing configuration files
- Running maintenance commands

**Common Mistake**

Trying to use `docker exec` on a stopped container.

---

### Question 7

**Question**

How do you view logs of a Docker container?

**Answer**

Use:

```bash
docker logs container_name
```

Follow logs continuously:

```bash
docker logs -f container_name
```

**Explanation**

Container logs display application output written to stdout and stderr.

**Used in Production**

The first step when investigating application failures.

---

### Question 8

**Question**

What is the purpose of the `docker inspect` command?

**Answer**

It displays detailed JSON information about Docker objects.

Example:

```bash
docker inspect mycontainer
```

**Explanation**

It provides information such as:

- IP Address
- Mounted volumes
- Environment variables
- Network settings
- Container configuration

**Used in Production**

Used when troubleshooting networking, storage, and container configuration issues.

---

### Question 9

**Question**

What is the difference between `docker stop`, `docker start`, and `docker restart`?

**Answer**

Stop container:

```bash
docker stop container_name
```

Start stopped container:

```bash
docker start container_name
```

Restart running container:

```bash
docker restart container_name
```

**Explanation**

These commands manage the lifecycle of existing containers.

**Used in Production**

Restarting applications after configuration changes or maintenance.

**Common Mistake**

Using `docker run` instead of `docker start`, which creates a new container instead of starting the existing one.

---

### Question 10

**Question**

What is the difference between `docker rm` and `docker rmi`?

**Answer**

Remove container:

```bash
docker rm container_name
```

Remove image:

```bash
docker rmi image_name
```

**Explanation**

Containers and images are different Docker objects.

Containers must usually be removed before deleting their associated images.

**Used in Production**

Cleaning unused Docker resources.

**Common Mistake**

Trying to delete an image that is still being used by a container.

---

### Question 11

**Question**

What are the purposes of the following Docker commands?

- `docker volume`
- `docker network`
- `docker compose`
- `docker tag`
- `docker push`

**Answer**

**docker volume**

Manage persistent storage.

Example:

```bash
docker volume ls
```

**docker network**

Manage Docker networks.

Example:

```bash
docker network ls
```

**docker compose**

Deploy multi-container applications.

Example:

```bash
docker compose up -d
```

**docker tag**

Assign another name or version to an image.

Example:

```bash
docker tag myapp:v1 myrepo/myapp:v1
```

**docker push**

Upload an image to a registry.

Example:

```bash
docker push myrepo/myapp:v1
```

**Explanation**

These commands are used extensively in production for storage management, networking, application deployment, image versioning, and CI/CD automation.

---

## Scenario-Based Interview Questions

### Scenario 1

**Question**

You receive a deployment request, but the required Docker image is not available on the server. What would you do?

**Answer**

Download the image:

```bash
docker pull repository/image:tag
```

Verify:

```bash
docker images
```

**Explanation**

The image must exist locally before containers can be created.

---

### Scenario 2

**Question**

Your application container is not accessible after deployment. Which Docker commands would you use to troubleshoot?

**Answer**

Check running containers:

```bash
docker ps
```

View logs:

```bash
docker logs container_name
```

Inspect configuration:

```bash
docker inspect container_name
```

**Explanation**

These commands verify whether the container is running, identify application errors, and confirm networking and port mappings.

---

### Scenario 3

**Question**

A developer requests access inside a running container to verify configuration files. Which command should you use?

**Answer**

```bash
docker exec -it container_name bash
```

or

```bash
docker exec -it container_name sh
```

**Explanation**

`docker exec` provides interactive access without interrupting the running application.

---

### Scenario 4

**Question**

Your Docker host is running out of disk space because of unused containers and images. How would you resolve the issue?

**Answer**

Remove stopped containers:

```bash
docker rm container_name
```

Remove unused images:

```bash
docker rmi image_name
```

Optionally:

```bash
docker system prune
```

**Explanation**

Regular cleanup prevents storage exhaustion on production Docker hosts.

---

### Scenario 5

**Question**

Your CI pipeline successfully builds an image, but the deployment server cannot pull it. What should you verify?

**Answer**

Check:

- Image was tagged correctly
- Image was pushed successfully

```bash
docker push repository/image:tag
```

Verify repository and authentication.

**Explanation**

Images must exist in the registry before deployment servers can pull them.

---

### Scenario 6

**Question**

A configuration change requires restarting an existing container without creating a new one. Which command should you use?

**Answer**

```bash
docker restart container_name
```

**Explanation**

Restarting preserves the existing container while applying runtime changes where appropriate.

---

### Scenario 7

**Question**

A teammate accidentally starts multiple duplicate containers by repeatedly using `docker run`. How could this have been avoided?

**Answer**

If the container already exists:

```bash
docker start container_name
```

instead of:

```bash
docker run
```

**Explanation**

`docker run` creates a new container every time, whereas `docker start` starts an existing one.

---

### Scenario 8

**Question**

You need to deploy a web application along with a MySQL database using a single command. Which Docker feature would you use?

**Answer**

Docker Compose.

Example:

```bash
docker compose up -d
```

**Explanation**

Docker Compose manages multiple related containers using a single YAML file.

---

### Scenario 9

**Question**

Your application stores uploaded files inside a container. After recreating the container, all uploads are lost. How would you fix this?

**Answer**

Create and mount a Docker volume.

Example:

```bash
docker volume create app-data
```

Mount it:

```bash
docker run -v app-data:/app/uploads myapp
```

**Explanation**

Volumes provide persistent storage independent of the container lifecycle.

---

### Scenario 10

**Question**

Your CI/CD pipeline builds an application, pushes the image to Docker Hub, and deploys it to production. Describe the sequence of Docker commands involved.

**Answer**

Typical workflow:

Build image:

```bash
docker build -t myapp:v1 .
```

Tag image:

```bash
docker tag myapp:v1 username/myapp:v1
```

Login:

```bash
docker login
```

Push image:

```bash
docker push username/myapp:v1
```

Deployment server:

```bash
docker pull username/myapp:v1
docker run -d username/myapp:v1
```

**Explanation**

This is the standard Docker CI/CD workflow followed by most organizations for containerized application deployment.
