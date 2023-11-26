# Go Challenge for FullCycle Course

## Overview

This repository contains a Go application developed as a part of the "Desafio Go" (Go Challenge) from the Docker module in the FullCycle 3.0 course.

## Challenge Requirements

- The Go application must display the message: "`FullCycle rocks!`"
- The resulting Docker image size must be under 2MB.

## Project Structure

- `main.go`: The Go source file that contains the application code.
- `go.mod`: Specifies the Go module name and version (_This project does not have any external dependencies_).
- `Dockerfile.dev`: The Docker configuration file used to build the image for local development purposes.
- `Dockerfile.prod`: The Docker configuration file used to build the image for a production environment.

## Instructions

To build and run this application, follow these steps:

### Development Environment

#### Building the Docker Image

```bash
docker build -f Dockerfile.dev -t gasscoelho/fullcycle-dev .
``` 

This will create a Docker image named `gasscoelho/fullcycle-dev`.

#### Running the Docker Container

```bash
docker run --rm --mount type=bind,source="$(pwd)",target="/workspace" -it gasscoelho/fullcycle-dev bash
```

This command will run the following:
- **Interactive TTY Mode (-it):** Opens an interactive terminal session within the container, allowing us to execute commands directly.
- **Volume Mounting (--mount):** Synchronizes the contents of the current host directory (`$(pwd)`) with the `/workspace` directory in the container. Changes made in one location are reflected in the other.
- **Temporary Container (--rm):** Ensures the container is automatically removed after it's stopped.

#### Running the Go application

```bash
go run main.go
```

The command above will **compile** and **run** the application code.

### Production Environment

#### Building the Docker Image

```bash
docker build -f Dockerfile.prod -t gasscoelho/fullcycle .
``` 

This will create a Docker image named `gasscoelho/fullcycle`.

#### Running the Docker Container

```bash
docker run --rm gasscoelho/fullcycle
```

This command runs the container and outputs "`FullCycle rocks!!`" to the terminal.

## Production Image on Docker Hub

The production-ready version of this application's Docker image is available on Docker Hub for public use.

```bash
docker pull gasscoelho/fullcycle-prod
```

This command will download the latest version of the production image to the local machine.

> [!WARNING]  
> Please note that this image may be removed in case of inactivity. If that happens, we will need to build the production version locally using the Dockerfile.
