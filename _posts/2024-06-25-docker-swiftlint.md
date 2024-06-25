---
toc: true
layout: post
comments: true
description: Use swiftlint from docker inside
categories: [markdown, tech]
title: swiftlint inside docker
---

## Setting Up Docker
Setting up Docker on your machine involves a few straightforward steps. Here’s a guide on how to install Docker and get it up and running on different operating systems.

### Installing Docker on macOS

1. **Download Docker Desktop**:
   - Go to the [Docker Desktop for Mac](https://www.docker.com/products/docker-desktop) download page.
   - Click the download button to get the Docker Desktop installer.

2. **Install Docker Desktop**:
   - Open the downloaded `.dmg` file.
   - Drag the Docker icon to the Applications folder.

3. **Run Docker Desktop**:
   - Go to your Applications folder and open Docker.
   - Docker will start and you will see the Docker icon in the menu bar.
   - You might be asked to authorize Docker with your system password.

4. **Verify Installation**:
   - Open a terminal and run:
     ```sh
     docker --version
     ```
   - You should see the Docker version information.

### Running Docker

After installing Docker, you can start using it to manage containers and images. Here’s a basic example of running an Ubuntu container interactively.

1. **Pull the Ubuntu Image**:
   ```sh
   docker pull ubuntu
   ```

2. **Run an Ubuntu Container**:
   ```sh
   docker run -it ubuntu
   ```

   - `-it`: Runs the container in interactive mode with a terminal.

3. **Exit the Container**:
   - To exit the container, you can simply type `exit` in the terminal.

To use a Docker image of SwiftLint with your local Swift files, you need to map your local directory containing the Swift files to the container and run SwiftLint inside the container. Here’s a step-by-step guide to achieve this:

## SwiftLint
### Pull the SwiftLint Docker Image

First, pull the SwiftLint image from Docker Hub:
```sh
docker pull realm/swiftlint
```

### Run the SwiftLint Docker Container

Next, run the SwiftLint container and mount your local directory containing the Swift files to the container. Use the `-v` option to bind mount a volume and the `-w` option to set the working directory inside the container.

Assuming your Swift files are in a directory called `my-swift-project`, you can use the following command:
```sh
docker run --rm -v "$(pwd)/my-swift-project:/mnt" -w /mnt realm/swiftlint swiftlint
```

### Explanation

- `docker run`: Runs a new container.
- `--rm`: Automatically removes the container when it exits.
- `-v "$(pwd)/my-swift-project:/mnt"`: Mounts the local `my-swift-project` directory to `/mnt` in the container. `$(pwd)` is a shell command that prints the current working directory.
- `-w /mnt`: Sets the working directory inside the container to `/mnt`.
- `realm/swiftlint`: The name of the Docker image.
- `swiftlint`: The command to run inside the container (in this case, it runs SwiftLint).

### Full Example

Let’s say you have a directory structure like this:
```
my-swift-project/
  ├── File1.swift
  ├── File2.swift
  └── ...
```

You can navigate to the parent directory of `my-swift-project` and run the command:
```sh
cd path/to/parent-directory
docker run --rm -v "$(pwd)/my-swift-project:/mnt" -w /mnt realm/swiftlint swiftlint
```

This command will run SwiftLint on all Swift files in the `my-swift-project` directory.

### Running SwiftLint with Additional Options

If you want to run SwiftLint with additional options or commands, you can pass them at the end of the Docker command. For example, to run SwiftLint with the `autocorrect` option, use:
```sh
docker run --rm -v "$(pwd)/my-swift-project:/mnt" -w /mnt realm/swiftlint swiftlint autocorrect
```

### Summary

1. **Pull the SwiftLint Docker image**:
   ```sh
   docker pull realm/swiftlint
   ```

2. **Run SwiftLint on your local Swift files**:
   ```sh
   docker run --rm -v "$(pwd)/my-swift-project:/mnt" -w /mnt realm/swiftlint swiftlint
   ```

By following these steps, you can easily integrate SwiftLint with your local Swift files using Docker.
