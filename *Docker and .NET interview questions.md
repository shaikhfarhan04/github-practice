These are common **Docker and .NET interview questions**. Below are concise answers suitable for interviews, along with examples.

---

# 1. What is a Multi-Stage Dockerfile?

A **Multi-Stage Dockerfile** uses multiple `FROM` statements to separate the **build environment** from the **runtime environment**.

* **Build stage:** Uses the .NET SDK image to restore packages, build, and publish the application.
* **Runtime stage:** Uses the smaller ASP.NET Runtime image to run the published application.

### Example

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build

WORKDIR /src
COPY . .
RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:10.0

WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet","app.dll"]
```

**Interview Answer:**
A Multi-Stage Dockerfile separates the build and runtime stages, producing a smaller, more secure, and production-ready Docker image.

---

# 2. Why is Multi-Stage better than a Single-Stage Dockerfile?

| Single Stage               | Multi Stage                    |
| -------------------------- | ------------------------------ |
| Contains SDK and runtime   | Contains only runtime          |
| Large image size           | Smaller image                  |
| Slower deployment          | Faster deployment              |
| More security risks        | More secure                    |
| Includes unnecessary files | Includes only published output |

**Example**

* Single-stage image: **1.5 GB**
* Multi-stage image: **250 MB**

**Interview Answer:**
Multi-stage builds reduce image size, improve security, speed up deployment, and remove unnecessary build tools from the final image.

---

# 3. Difference between SDK and ASP.NET Runtime images?

| SDK Image            | ASP.NET Runtime Image |
| -------------------- | --------------------- |
| Used for development | Used for running apps |
| Includes compiler    | No compiler           |
| Includes CLI         | No CLI                |
| Larger               | Smaller               |
| Used for build       | Used in production    |

Examples:

```dockerfile
mcr.microsoft.com/dotnet/sdk:10.0
```

```dockerfile
mcr.microsoft.com/dotnet/aspnet:10.0
```

**Interview Answer:**
The SDK image is used to build and publish applications, while the ASP.NET Runtime image is used only to run published applications.

---

# 4. Why do we use `dotnet publish` instead of `dotnet build` in Docker?

`dotnet build`

* Compiles the project
* Generates DLL files
* Keeps build artifacts

`dotnet publish`

* Compiles the application
* Packages everything needed to run
* Creates optimized output for deployment

Example:

```bash
dotnet publish -c Release -o /app
```

**Interview Answer:**
`dotnet publish` creates a deployable package with all required files, making it the preferred choice for Docker images.

---

# 5. What is the purpose of `COPY --from=build`?

It copies files from a previous build stage into the final image.

Example:

```dockerfile
COPY --from=build /app .
```

Instead of copying the source code, it copies only the published application.

**Interview Answer:**
It transfers only the required output from the build stage to the runtime stage, reducing image size.

---

# 6. What is the difference between `EXPOSE` and `-p`?

### EXPOSE

Inside Dockerfile

```dockerfile
EXPOSE 8080
```

* Documents which port the container listens on.
* Does **not** publish the port.

### -p

While running the container

```bash
docker run -p 8080:8080 image
```

* Maps a host port to a container port.
* Makes the application accessible from outside the container.

**Interview Answer:**
`EXPOSE` is documentation inside the image, while `-p` actually publishes the port to the host.

---

# 7. Why do we use `WORKDIR`?

It sets the default working directory for subsequent Dockerfile instructions.

Example

```dockerfile
WORKDIR /app
```

Instead of writing

```dockerfile
RUN cd /app
```

every time.

**Interview Answer:**
`WORKDIR` simplifies Dockerfiles by setting the current working directory for all following instructions.

---

# 8. Difference between `ENTRYPOINT` and `CMD`?

### ENTRYPOINT

Defines the main executable.

```dockerfile
ENTRYPOINT ["dotnet","app.dll"]
```

Cannot be easily overridden without using `--entrypoint`.

---

### CMD

Provides default arguments or commands.

```dockerfile
CMD ["--urls","http://+:8080"]
```

Can be overridden when running the container.

---

### Together

```dockerfile
ENTRYPOINT ["dotnet","app.dll"]
CMD ["--urls","http://+:8080"]
```

Running

```bash
docker run image
```

uses the default URL.

Running

```bash
docker run image --urls http://+:9090
```

overrides only the `CMD` arguments.

**Interview Answer:**
`ENTRYPOINT` defines the container's main process, while `CMD` supplies default arguments that can be overridden.

---

# 9. Why is `docker buildx` used?

`buildx` is Docker's extended build tool.

Features:

* Multi-platform builds (AMD64, ARM64)
* Better caching
* Faster builds
* Advanced build features

Example

```bash
docker buildx build --load -t app .
```

**Interview Answer:**
`docker buildx` provides advanced build capabilities, including multi-platform image creation and improved build performance.

---

# 10. What are bridge, host, and overlay Docker networks?

### Bridge Network

Default network for standalone containers.

```bash
docker network create mynetwork
```

Containers on the same bridge can communicate.

---

### Host Network

Container shares the host's network stack.

No NAT or port mapping.

Mostly used on Linux.

---

### Overlay Network

Used in Docker Swarm.

Allows containers on different hosts to communicate securely.

**Interview Answer:**

* **Bridge:** Default network for standalone containers.
* **Host:** Shares the host's network stack.
* **Overlay:** Connects containers across multiple Docker hosts.

---

# 11. How do you inspect a running container?

```bash
docker inspect container_name
```

Useful commands:

```bash
docker ps
```

```bash
docker logs container_name
```

```bash
docker exec -it container_name sh
```

**Interview Answer:**
Use `docker inspect` for detailed metadata, `docker logs` for application logs, and `docker exec` to access the running container.

---

# 12. How do you debug a container that exits immediately?

1. Check logs:

```bash
docker logs container_name
```

2. Inspect exit code:

```bash
docker inspect container_name
```

3. Start an interactive shell (if possible):

```bash
docker run -it image sh
```

4. Verify the `ENTRYPOINT` and application configuration.

**Interview Answer:**
Start by reviewing container logs, inspect the exit status, and run the container interactively to identify configuration or startup issues.

---

# 13. How do you reduce Docker image size?

* Use Multi-Stage builds.
* Use smaller base images (for example, ASP.NET Runtime instead of SDK).
* Remove temporary files.
* Combine related `RUN` commands to reduce layers.
* Add a `.dockerignore` file to exclude unnecessary files.
* Copy only required files into the image.

**Interview Answer:**
Reduce image size by using Multi-Stage builds, lightweight base images, `.dockerignore`, and by excluding unnecessary files and dependencies.

---

# 14. How do you version Docker images using tags?

Create tags during build:

```bash
docker build -t myapp:v1 .
```

Tag an existing image:

```bash
docker tag myapp:v1 myapp:v2
```

Push a tagged image:

```bash
docker push username/myapp:v1
```

List images:

```bash
docker images
```

**Interview Answer:**
Docker tags provide versioning for images, such as `v1`, `v2`, or `latest`, making deployments and rollbacks easier.

---

# 15. What is the difference between `dotnet restore`, `dotnet build`, `dotnet publish`, and `dotnet run`?

| Command          | Purpose                                                 | Typical Usage                                      |
| ---------------- | ------------------------------------------------------- | -------------------------------------------------- |
| `dotnet restore` | Downloads NuGet packages and project dependencies       | Before the first build or when dependencies change |
| `dotnet build`   | Compiles the project into assemblies (DLLs)             | Development and CI builds                          |
| `dotnet publish` | Produces an optimized, deployable set of files          | Docker images and production deployments           |
| `dotnet run`     | Builds (if needed) and immediately runs the application | Local development and testing                      |

### Typical Docker Build Flow

```bash
dotnet restore
dotnet build
dotnet publish -c Release -o /app
```

### Local Development Flow

```bash
dotnet restore
dotnet run
```

**Interview Answer:**

* `restore` downloads dependencies.
* `build` compiles the application.
* `publish` creates deployment-ready output.
* `run` builds (if necessary) and starts the application for development.
