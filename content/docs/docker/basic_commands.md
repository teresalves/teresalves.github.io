---
title: "Basic Commands"
description: "Guides lead a user through a specific task they want to accomplish, often with a sequence of steps."
supertitle: "Docker"
summary: ""
date: 2023-09-07T16:04:48+02:00
lastmod: 2023-09-07T16:04:48+02:00
draft: false
weight: 310
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


`docker --version`: Displays the installed version of Docker.

`docker pull <image>`: Downloads a Docker image from a registry.

`docker images`: Lists all the Docker images on the local system.

`docker run <image>`: Creates and starts a new container from an image.

`docker ps`: Lists currently running containers.

`docker ps -a`: Lists all containers, including stopped ones.

`docker stop <container>`: Stops a running container.

`docker rm <container>`: Removes a stopped container.

`docker rmi <image>`: Removes a Docker image from the local system.

`docker exec -it <container> <command>`: Runs a command inside a running container.

`docker logs -f <container>`: Displays the logs of a container - the `-f` means it will continuously show the logs until you stop it.

`docker build -t <name> <path>`: Builds a Docker image from a Dockerfile. `-t`is the image name or tag. The path can simply be `.`. If the Dockerfile is instead called .Dockerfile-dev or something, add `-f .Dockerfile-dev`

`docker inspect <container>`: Displays detailed information about a container or image.

`docker network ls`: Lists all Docker networks.

`docker volume ls`: Lists all Docker volumes.
