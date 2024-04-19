Docker is a platform that uses containers to make application development, deployment, and maintenance easier. Applications can run reliably across several contexts by using containers, which package them along with all of their dependencies. Scalability, resource efficiency, and management effectiveness are all increased by Docker's containerization technology, which makes application development, testing, and deployment fast and dependable.
Learn more [docs.docker.com/get-started/overview/](https://docs.docker.com/get-started/overview/)

*Youtube videos to learn more:*
- [# Docker in 100 Seconds - Fireship](https://www.youtube.com/watch?v=Gjnup-PuquQ)
## Installation

Follow the link to Install Git for respective OS:
- [Install for Linux](https://docs.docker.com/desktop/install/linux-install/)
- [Install for macOS](https://docs.docker.com/desktop/install/mac-install/)
- [Install for Windows](https://docs.docker.com/desktop/install/windows-install/)

Login to Docker Hub [hub.docker.com/](https://hub.docker.com/)
- Create a repo if needed

## Jump to
- [Docker Login](#docker-login)
- [Create Images](#create-images)
- [Docker Hub](#docker-hub)
- [Start Docker deamon](#start-docker-deamon)
- [Create Containers](#create-containers)
- [Simple Dockerfile for Nodejs server](#simple-dockerfile-for-nodejs-server)
- [Simple Dockerfile for Python file](#simple-dockerfile-for-python-file)

## Docker commands --list

### Docker Login

Provide username and password create in Docker Hub

    docker login

    docker logout

### Create Images
Build an Image from a Dockerfile

    docker build -t <image-name>

List local images

    docker images

Delete an image

    docker rmi <image-name>

Remove all unused images

    docker image prune

### Docker Hub

Publish an image to Docker Hub

    docker push <username>/<image-name>

Search for other images

    docker search <image-name>

Pull an image from Docker Hub

    docker pull <image-name>

### Start Docker deamon

    docker -d

### Create Containers

Create a container and run with the image

    docker run --name <container-name> <image-name>

Run and push a container with container's port

    docker run -p <host-port>:<container-port>

Start or Stop container

    docker start <container-name>
    docker stop <container-name>

Remove a stopped container

    docker rn <container-name>

Open a shell inside running container

    docker exec -it <container-name> sh

Inspect a running container

    docker inspect <container-name>

List currently running containers

    docker ps
    docker ps -a

View container usage status

    docker container status


### Simple Dockerfile for Nodejs server

dockerfile

    FROM node:latest
    WORKDIR /app
    COPY package.json /app
    RUN npm install
    COPY . /app
    EXPOSE 3000
    CMD ["node", "server.js"]

- The container must run in port 3000, to run the Nodejs server.

### Simple Dockerfile for Python file

dockerfile

    FROM python:latest
    WORKDIR /app
    COPY . /app
    CMD ["python", "bmi.py"]

- The container must run in a interactive mode, to enter input values.
