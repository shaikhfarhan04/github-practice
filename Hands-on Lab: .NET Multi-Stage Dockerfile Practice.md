Below is a **real-world hands-on lab** that covers all the topics in your assignment **plus additional Docker and .NET concepts** that are commonly asked in DevOps interviews.

---

# Hands-on Lab: .NET Multi-Stage Dockerfile Practice

**Objective**

Build a .NET ASP.NET application, containerize it using a Multi-Stage Dockerfile, test it locally, push it to Docker Hub, and practice Docker networking.

**Prerequisites**

* Windows 10/11
* VS Code
* Docker Desktop
* Git
* .NET SDK
* Docker Hub Account
* Internet Connection

---

# Phase 1 - Install .NET SDK

### Windows

Download the .msi installer from

[https://dotnet.microsoft.com/](https://dotnet.microsoft.com/)

Install it.

Verify installation.

```powershell
dotnet --version
```

Expected

```
10.x.x
```

---

### Ubuntu

```bash
sudo apt update

sudo apt install dotnet-sdk-aot-10.0 -y

dotnet --version
```

---

# Phase 2 - Clone Project

```bash
git clone https://github.com/atulkamble/Dockerfiles.git

cd Dockerfiles/08-dotnet-aspnet-app
```

Pull latest changes

```bash
git pull
```

---

# Phase 3 - Open in VS Code

```bash
code .
```

Observe project structure.

```
08-dotnet-aspnet-app/

Program.cs

Dockerfile

app.csproj

Properties/

appsettings.json
```

---

# Phase 4 - Run Application Without Docker

Restore packages

```bash
dotnet restore
```

Build project

```bash
dotnet build
```

Run application

```bash
dotnet run
```

Expected

```
Now listening on:

http://localhost:5000
```

Open browser

```
http://localhost:5000
```

---

# Phase 5 - Understand the Dockerfile

Open

```
Dockerfile
```

Example Multi-Stage Dockerfile

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:10.0

WORKDIR /app

COPY --from=build /app .

EXPOSE 8080

ENTRYPOINT ["dotnet","app.dll"]
```

Understand

Stage 1

* SDK Image
* Restore packages
* Build project
* Publish binaries

Stage 2

* Runtime Image
* Smaller image
* Production ready

---

# Phase 6 - Login Docker Hub

```bash
docker login
```

or

```bash
docker login -u YOUR_USERNAME
```

Verify

```bash
docker info
```

---

# Phase 7 - Build Docker Image

```bash
docker buildx build -t docker.io/YOUR_USERNAME/dotnetapp:latest --load .
```

Verify

```bash
docker images
```

---

# Phase 8 - Run Container

```bash
docker run -d -p 8080:8080 --name dotnet-container YOUR_USERNAME/dotnetapp:latest
```

Verify

```bash
docker ps
```

Visit

```
http://localhost:8080
```

---

# Phase 9 - Container Inspection

Container logs

```bash
docker logs dotnet-container
```

Inspect

```bash
docker inspect dotnet-container
```

Container processes

```bash
docker top dotnet-container
```

Execute inside container

```bash
docker exec -it dotnet-container sh
```

Exit

```bash
exit
```

---

# Phase 10 - Push Image

```bash
docker push docker.io/YOUR_USERNAME/dotnetapp:latest
```

Verify image appears in Docker Hub.

---

# Phase 11 - Remove Container

```bash
docker stop dotnet-container

docker rm dotnet-container
```

---

# Phase 12 - Docker Network Practice

View help

```bash
docker network --help
```

List networks

```bash
docker network ls
```

Create network

```bash
docker network create mynetwork
```

Verify

```bash
docker network ls
```

Inspect network

```bash
docker network inspect mynetwork
```

Run application on custom network

```bash
docker run -d \
--name dotnetapp \
--network mynetwork \
-p 8080:8080 \
YOUR_USERNAME/dotnetapp:latest
```

Verify

```bash
docker inspect dotnetapp
```

Remove

```bash
docker stop dotnetapp

docker rm dotnetapp

docker network rm mynetwork
```

Verify

```bash
docker network ls
```

---

# Phase 13 - Docker Image Management

List images

```bash
docker images
```

Image history

```bash
docker history YOUR_USERNAME/dotnetapp
```

Inspect image

```bash
docker inspect YOUR_USERNAME/dotnetapp
```

Remove image

```bash
docker rmi YOUR_USERNAME/dotnetapp
```

---

# Phase 14 - Practice Multi-Stage Build

Compare image sizes.

Single Stage

```
FROM sdk
```

Multi Stage

```
SDK → Runtime
```

Observe

```bash
docker images
```

Questions

* Which image is larger?
* Why?
* Which one should be deployed?

---

# Phase 15 - Modify Application

Open

```
Program.cs
```

Change message.

Example

```
Hello Docker

↓

Hello DevOps Engineers
```

Rebuild

```bash
docker buildx build -t docker.io/YOUR_USERNAME/dotnetapp:v2 --load .
```

Run

```bash
docker run -d -p 8081:8080 YOUR_USERNAME/dotnetapp:v2
```

Verify

```
http://localhost:8081
```

---

# Additional Practice (Recommended)

## Tag Image

```bash
docker tag YOUR_USERNAME/dotnetapp:latest YOUR_USERNAME/dotnetapp:v1
```

---

## Run Multiple Containers

```bash
docker run -d -p 8081:8080 --name app1 YOUR_USERNAME/dotnetapp

docker run -d -p 8082:8080 --name app2 YOUR_USERNAME/dotnetapp
```

---

## Rename Container

```bash
docker rename app1 production-app
```

---

## Restart Container

```bash
docker restart production-app
```

---

## View Resource Usage

```bash
docker stats
```

---

## Copy File From Container

```bash
docker cp production-app:/app .
```

---

## Save Docker Image

```bash
docker save -o dotnetapp.tar YOUR_USERNAME/dotnetapp
```

---

## Load Docker Image

```bash
docker load -i dotnetapp.tar
```

---

## Clean Up

```bash
docker stop $(docker ps -aq)

docker rm $(docker ps -aq)

docker image prune -a

docker network prune

docker volume prune

docker system prune -a
```

---

# Interview Questions to Practice

1. What is a Multi-Stage Dockerfile?
2. Why is Multi-Stage better than a Single-Stage Dockerfile?
3. Difference between SDK and ASP.NET Runtime images?
4. Why do we use `dotnet publish` instead of `dotnet build` in Docker?
5. What is the purpose of `COPY --from=build`?
6. What is the difference between `EXPOSE` and `-p`?
7. Why do we use `WORKDIR`?
8. Difference between `ENTRYPOINT` and `CMD`?
9. Why is `docker buildx` used?
10. What are bridge, host, and overlay Docker networks?
11. How do you inspect a running container?
12. How do you debug a container that exits immediately?
13. How do you reduce Docker image size?
14. How do you version Docker images using tags?
15. What is the difference between `dotnet restore`, `dotnet build`, `dotnet publish`, and `dotnet run`?

This lab covers your assignment points while adding practical Docker operations, image management, networking, container debugging, cleanup, and interview-oriented tasks that are valuable for DevOps and Docker interviews.
