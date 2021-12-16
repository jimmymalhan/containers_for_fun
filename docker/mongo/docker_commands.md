# Docker System Design
## To check the images publically
 - doesn't require a access
 - doesn't require a authentication

https://hub.docker.com/search?type=image

## Before containers
Developers -> configuration/dependency of the server needed (JAR file) -> Operations (textual guide of deployment)

Cons:
- Dependency versions conflicts
- misunderstanding of the deployment process

## After containers
- Developers and operations work together to package the application in a container
- No environment configuration needed on server - except Docker Runtime

## Container contains:
configuration, JAR, dependencies -> operations

## Docker run
```
docker run postgres:9.6 -p 5432:5432
```
### it will check if the image is available in the local repository and if not it will pull it from the registry

## Layer
### it will download the image based on the layers
- database layer
- application layer
- configuration layer
- dependencies layer

### All the lines in the Dockerfile is equivalent to the layers

# Dockerfile
################ DockerFile ################
```bash
FROM python:3.7 # Copy the static files to the web root
WORKDIR /app
COPY . /app


# add permissions to the user
# USER 1000
# RUN chown -R 1000:1000 /app && chmod -R 644 /app

# Update the image and install vim
RUN apt-get update && apt-get install -y \ 
    vim

# Install Python dependencies
COPY requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt

# EXPOSE 8080
CMD ["python", "app.py"] 
# RUN python3 app.py
```
# Docker Commands
################ Docker Commands ################

## 1. Docker Build/Run
#### Build custom image
```
docker build -t test123 .
```
#### Run generic/custom image
```
docker run -d -p <host_port/laptop_port>:<container_port> --name <custom_image_name> <image_name to pull from dockerHub>

docker run -d -p 6001:6379 --name redis-older redis:4.0
```
#### Check the images
```
docker images
```

## Troubleshooting:
* `Restart the container`
```
- docker ps # to get the container id
- docker stop <container_id>
- docker ps -a # to check the container is stopped
- docker start <container_id>
                or
- docker restart <container_id>
```
* Define the port mapping in the command line
```
- docker ps
- docker stop <container_id>
- docker ps -a # container is stopped
- docker run -d -p <host_port/laptop_port>:<container_port> <image_name>
- docker run -d -p 6000:6379 redis:4.0


`docker ps` # list all containers
`docker ps -a` # list of running and stop containers
`docker ps -l` # list all running containers
```
################ Debugging Containers ################
```
docker ps # get the container id
docker logs <container_id>
or
docker logs <container_name>

docker exec -it <container_id> /bin/bash
or
docker exec -it <container_name> /bin/bash

# After getting into the container run the following commands:
# env # check the environment variables
```

* Remove image:
```
# Remove docker container
docker container rm <container_id>

# Remove docker image
docker image rm 3d6879c31143  --force 
```

* Kill all containers and remove them from the system and images:
```
docker rm -f $(docker ps -a -q) # remove all containers
docker rmi $(docker images -q) # remove all images
```

* How to check url of the flask application in the container?
```
docker exec -it <container name> curl -I http://localhost:80/
```
############ Other commands ############
- `docker create` # create container
- `docker build` # build a new image from dockerfile
- `docker inspect [container ID]` # Get more info about running container
- `docker push` # push your image to docker repo
- `docker pull` # download an image locally from docker repo
- `docker commit` # create an image from container
- `docker volume` # create a docker volume
- `docker network` # create a docker network
