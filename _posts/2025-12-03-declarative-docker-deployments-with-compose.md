---
toc: false
layout: post
comments: true
categories: [docker, deployment, tech, tools]
title: "From Shell Scripts to Services: A Docker Compose Story"
---

When you're first getting started with Docker, it's common to manage your containers with a series of shell commands. You might even write a shell script to automate the process, just like I did. But as your application grows, this imperative approach can become cumbersome. In this post, I'll share my journey from a manual `deploy.sh` script to a clean, declarative setup using `docker-compose`.

## The Old Way: An Imperative Shell Script

My project is a simple URL shortener application that uses a Python backend and a Redis database. To deploy it, I wrote a `deploy.sh` script. It automated building the image, setting up the network, and running the containers.

Here’s what it looked like:

```bash
#!/bin/bash
set -e

IMAGE_NAME="url-shortener"
APP_CONTAINER_NAME="url-shortener-app"
REDIS_CONTAINER_NAME="redis-server"
NETWORK_NAME="url-net"

# Build the image
echo "Building the '${IMAGE_NAME}' Docker image..."
docker build -t ${IMAGE_NAME} .

# Set up the network
if [ -z "$(docker network ls --filter name=^${NETWORK_NAME}$ --format=\"{{ .Name }}\")" ]; then
    docker network create ${NETWORK_NAME}
fi

# Stop and remove old containers
docker stop ${APP_CONTAINER_NAME} >/dev/null 2>&1 || true
docker rm ${APP_CONTAINER_NAME} >/dev/null 2>&1 || true
docker stop ${REDIS_CONTAINER_NAME} >/dev/null 2>&1 || true
docker rm ${REDIS_CONTAINER_NAME} >/dev/null 2>&1 || true

# Start Redis
docker run -d \
    --name ${REDIS_CONTAINER_NAME} \
    --network ${NETWORK_NAME} \
    redis

# Start the App
docker run -d \
    -p 8000:8000 \
    --network ${NETWORK_NAME} \
    -e REDIS_URL=redis://${REDIS_CONTAINER_NAME}:6379/0 \
    --name ${APP_CONTAINER_NAME} \
    ${IMAGE_NAME}
```

This script gets the job done, but it’s **imperative**. It’s a list of *how* to do something. It’s verbose, requires manual error handling (like the network check), and isn’t easy to read at a glance.

## The New Way: A Declarative Docker Compose File

Docker Compose allows you to define your application's services, networks, and volumes in a single, declarative YAML file. You describe the desired **end state**, and Docker Compose figures out how to get there.

I replaced my entire `deploy.sh` script with this one `docker-compose.yml` file:

```yaml
version: '3.8'

services:
  app:
    build: .
    container_name: url-shortener-app
    ports:
      - "8000:8000"
    environment:
      - REDIS_URL=redis://redis:6379/0
    depends_on:
      - redis
    networks:
      - url-net

  redis:
    image: redis
    container_name: redis-server
    networks:
      - url-net

networks:
  url-net:
    name: url-net
```

This file is much cleaner and easier to understand. It clearly defines the two services (`app` and `redis`), how the `app` should be built, and how they connect.

## The Benefits of the Declarative Approach

The advantages of this switch are immediate:

1.  **Simplicity**: Instead of running a script, I can now start my entire application with `docker-compose up -d` and stop it with `docker-compose down`.
2.  **Readability**: The YAML file is a clear, at-a-glance definition of my entire application stack.
3.  **Maintainability**: If I need to add a new service or change a configuration, I just edit the YAML file. No more wrestling with shell script logic.
4.  **Automation**: Docker Compose handles all the underlying work of creating networks, linking services, and managing container lifecycle.

## Conclusion

Moving from a shell script to a `docker-compose.yml` file was a fantastic improvement for my project. It simplified my deployment process and made my application's architecture much clearer. If you're still managing multi-container Docker applications with scripts, I highly recommend giving Docker Compose a try. It's a small change that makes a huge difference.


## Reference
- [url-shortener](https://github.com/Ian729/url-shortener/)
