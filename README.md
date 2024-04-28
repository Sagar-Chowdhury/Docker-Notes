
![docker-logo-blue](https://github.com/Sagar-Chowdhury/Docker-Theory/assets/76145064/4ca3fffa-4239-4b8d-85a2-500f3dc6c626)

**Docker 🐳 – Solving Development Environment Headaches**

**Problem Statement**

* Replicating development environments across machines can be a pain, especially when dealing with different configurations and dependencies.
* Onboarding new developers gets tougher as they have to set up the entire development environment from scratch.

**Introduction to Docker**

Docker is here to save the day! It's a platform designed to make it super easy to build, package, and run your applications consistently in any environment.

**Key Components**

1. **Docker CLI (Command Line Interface):**  Your trusty tool for interacting with Docker. Use it to control containers, images, and more.
2. **Docker Engine:** The heart of Docker, responsible for running containers and managing images.
3. **Docker Hub:** A massive online repository filled with pre-built Docker images.

**Installation**

* Head to the official Docker website and download Docker Desktop for your operating system (includes everything you need - Engine, CLI, etc.): [https://www.docker.com/get-started](https://www.docker.com/get-started)

**Docker CLI: Your Swiss Army Knife**

| Command                | Description                                          |
| -----------------------| -----------------------------------------------------|
| `docker version`       | Check your installed Docker versions                  |
| `docker pull`          | Grab an image from a registry like Docker Hub         |
| `docker run`           | Create and start a new container from an image        |
| `docker ps`            | List all running containers                          |
| `docker ps -a`         | List all containers (running and stopped)            |
| `docker stop`          | Gracefully stop a running container                  |
| `docker kill`          | Forcefully stop a running container                   |
| `docker exec`          | Run a command inside a running container             |
| `docker images`        | Show the images you have locally                     |
| `docker rmi`           | Delete an image                                      |
| `docker build`         | Build a new image from a Dockerfile               |

**Example:**

```bash
docker run -it ubuntu 
```

* **-it:** Gives you an interactive session inside the container.
* **ubuntu:** The image to use. If you don't have it locally, Docker will download it.

**Images vs. Containers: The Analogy**

* **Image:** Think of it as a class definition in programming. It's the blueprint for what your application *could* be. Static and unchanging.
* **Container:** Like an object created from that class. A running instance of an image, where your application lives. You can run multiple containers from the same image.

**Port Mapping: Opening Doors**

To access your application from your machine, map your container's port to a port on your host:

```bash
docker run --publish 8080:80 <image_name> 
```
(Access your app on your browser at http://localhost:8080)

**Environment Variables: Flexible Configuration**

Pass environment variables at runtime:

```bash
docker run -e MYVAR1="value" --env MYVAR2=foo ubuntu bash
```

**Dockerizing a Node.js Application**

[Using Docker init these are created automatically](https://docs.docker.com/language/nodejs/containerize/)

1. **Dockerfile:** Instructions for building your image.

   ```dockerfile
   FROM node:latest # Base image
   WORKDIR /app     # Working directory inside container
   COPY package.json . 
   RUN npm install   
   COPY . .          # Copy your project files
   EXPOSE 8080       # Expose the port
   CMD ["node", "app.js"]  
   ```

2. **.dockerignore:** Excludes unnecessary files from your build.

3. **Build and Run:**

   ```bash
   docker build -t my-node-app .
   docker run -it -p 8080:8080 my-node-app
   ```


