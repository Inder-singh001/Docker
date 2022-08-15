# Docker
[Docker](https://docs.docker.com/) is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your host machine so you can deliver software quickly.Docker provides the ability to package and run an application in a loosely isolated environment called a container.Containers are lightweight and contain everything needed to run the application, so you do not need to rely on what is currently installed on the host.

## What is container
A **Container** is a box that process isolated environment on your machine from all other processes on the host machine.It is a platform where you can run the images.
- You can create, start, stop, move or delete a container using Docker.
- You can create many containers and run many software isolated on your machine from your host machine.
- It can be run on local machines, virtual machines or deployed to the cloud and is poratble i.e can rum on any OS.

## Images
An **image** is a read-only template with instructions. An image is a software which contains his whole libraries that are required to the user for usage of the software such as pyhton, mysql, mariaDB, redis, etc. You can also create your own images using dockerfile.

---

## Docker Manuals
#### Docker Desktop
[Docker Desktop](https://docs.docker.com/desktop) is the main interface where the user will interacte with docker. It provides a simple interface that enables you to manage all your containers, images, and environments.In Docker Desktop, you can:
- run
- stop
- remove  
- restart
- pull
- push \
  etc, the containers and images.
#### Docker Engine
[Docker Engine](https://docs.docker.com/engine) is an open source containerization technology for building and containerizing your applications.It creates and manages the work of the containers, images,volumes, and environments.
#### Docker Hub
A [Docker Hub](https://docs.docker.com/docker-hub) is a open-source software hub where you can find and share containers and images. It is a largest repository of container images with an array of content sources including container community developers, open source projects and independent software vendors (ISV) building and distributing their code in containers.

> To install Docker: \
  Refer to the link [Install Docker Desktop](https://docs.docker.com/desktop/install/ubuntu/)
  
---

### Some mainly used Docker Commands
- `docker --user Start docker-desktop` - To start the docker desktop
- `docker run` - run container in image locally or go to hub
- `docker ps` - lists the running container in docker desktop 
- `docker ps -a` - outputs all the container running or previously running(stopped)
- `docker stop <conatinername>` - stops the container
- `docker rm <containername>` - removes the container
- `docker images` - lists the images present in your dockre desktop
- `docker rmi <imagename>` - removes images
- `docker pull <imagename>` - pulls the image from docker hub
- `sudo service docker status` - tells the status of docker 
# DEMO
### Creating a simple container
Let's create a container using an image pulled from Docker Hub.Check the image you want to pull from Docker Hub.\
Open the terminal and start the docker then write
- `$ docker run -i -t --name mysql mysql` this will run container with an image MYSQL and download it from Docker Hub
- This will show an error that create a root password. However, MySQL requires a password to access databases. 
- Thus, again write the command
`docker run -it -e MYSQL_ROOT_PASSWORD=mysql --name mysql mysql`
> Unable to find image 'mysql:latest' locally \
  latest: Pulling from library/mysql \
  32c1bf40aba1: Pull complete \
  3ac22f3a638d: Pull complete \
  b1e7273ed05e: Pull complete \
  20be45a0c6ab: Pull complete \
  410a229693ff: Pull complete \
  1ce71e3a9b88: Pull complete \
  c93c823af05b: Pull complete \
  c6752c4d09c7: Pull complete \
  d7f2cfe3efcb: Pull complete \
  916f32cb0394: Pull complete \
  0d62a5f9a14f: Pull complete \
  Digest: sha256:ce2ae3bd3e9f001435c4671cf073d1d5ae55d138b16927268474fc54ba09ed79 \
  Status: Downloaded newer image for mysql:latest \

- Your container is ready for work!

### Creating a container with own image
Let's create a contianer by creating an image. For this
- Firstly, create a dockerfile, `cat > dockerfile << EOF`. You can also name the file in `<name>.dockerfile` or `dockerfile.<name>`.
- Write \
>  # syntax=docker/dockerfile:1 
  FROM python:3.8-slim-buster \
  WORKDIR /app \
  COPY requirements.txt requirements.txt \
  RUN pip3 install -r requirements.txt \
  COPY . . \
  CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]

 



[References Commands to use docker](https://docs.docker.com/reference/)


