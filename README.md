# Docker Commands

## Contents
- [Docker Commands](#docker-commands)
  - [Contents](#contents)
  - [Commands Container](#commands-container)
    - [Run a new container:](#run-a-new-container)
    - [List running containers:](#list-running-containers)
    - [Stop a running container:](#stop-a-running-container)
    - [Restart a running container:](#restart-a-running-container)
    - [Delete a container:](#delete-a-container)
  - [Commands Image](#commands-image)
    - [Initialize a new image:](#initialize-a-new-image)
    - [List images:](#list-images)
    - [Delete an images:](#delete-an-images)
    - [Pull an image from a remote repository:](#pull-an-image-from-a-remote-repository)
  - [Commands Network](#commands-network)
    - [List networks:](#list-networks)
    - [Create a new network:](#create-a-new-network)
    - [Connect a container to network:](#connect-a-container-to-network)
    - [Disconnect a container from network:](#disconnect-a-container-from-network)
    - [Remove a network:](#remove-a-network)
    - [Inspect a network:](#inspect-a-network)
  - [Commands Volume](#commands-volume)
    - [Initalize a new volume:](#initalize-a-new-volume)
    - [List volumes:](#list-volumes)
    - [Inspect a volume:](#inspect-a-volume)
  - [Commands Other](#commands-other)
    - [View logs of a container:](#view-logs-of-a-container)
    - [Execute a command in a running container:](#execute-a-command-in-a-running-container)
    - [Tag image:](#tag-image)
    - [Push an image:](#push-an-image)
    - [Delete containers, images, networks and volumes don't use:](#delete-containers-images-networks-and-volumes-dont-use)

## Commands Container
### Run a new container:
```
docker run -d --name <container_name> -p <host_port>:<container_port> <image_name>
```
* Run a new container in detached mode (`-d`).
* Example: `docker run -d --name my-nginx nginx`

### List running containers:
```
docker ps
```
* Lists all running containers.
* Add `-a` to see all containers, including stopped ones.

### Stop a running container:
```
docker stop <container_id|container_name>
```
* Stops a running container.

### Restart a running container:
```
docker restart <container_id|container_name>
```
* Restarts a running container.

### Delete a container:
```
docker rm <container_id|container_name>
```
* Deletes a stopped container.
* Use `-f` to force delete a running container.

## Commands Image
### Initialize a new image:
```
docker build -t <image_name>:<tag> <path_to_dockerfile>
```
* Builds a new image from a Dockerfile.
* Example: `docker build -t my-app:latest .`

### List images:
```
docker images
```
* Lists all images on the local machine.

### Delete an images:
```
docker rmi <image_id|image_name>
```
* Deletes a image.
* Use `-f` to force delete an image, which is in use by a container.

### Pull an image from a remote repository:
```
docker pull <image_name>:<tag>
```
* Pulls an image from Docker Hub or another registry.
* Example: `docker pull nginx:latest`.

## Commands Network
### List networks:
```
docker network ls
```
* Lists all Docker networks.

### Create a new network:
```
docker network create <network_name>
```

### Connect a container to network:
```
docker network connect <network_name> <container_name>
``` 

### Disconnect a container from network:
```
docker network disconnect <network_name> <container_name>
```

### Remove a network:
```
docker network rm <network_name>
```

### Inspect a network:
```
docker network inspect <network_name>
```
* Displays detailed information about a network.

## Commands Volume
### Initalize a new volume:
```
docker volume create <volume_name>
```
* Creates a new Docker volume.

### List volumes:
```
docker volume ls
```
* Lists all Docker volumes.

### Inspect a volume:
```
docker volume inspect <volume_name>
```
* Displays detailed information about a volume.

## Commands Other
### View logs of a container:
```
docker logs <container_id|container_name>
```
* Displays the logs of a container.
* Use `-f` to follow the logs in real-time.


### Execute a command in a running container:
```
docker exec -it <container_id|container_name> <command>
```
* Executes a command in a running container.
* Example: `docker exec -it my-nginx bash` to open a shell in the container.

### Tag image:
```
docker tag <image_name> <repository>/<image_name>:<tag>
```
* Tags a image to prepare for pushing it to a remote repository.
* Example: `docker tag my_app myrepo/my_app:latest`.

### Push an image:
```
docker push <repository>/<image_name>:<tag>
```
* Pushes a image to a remote repository.
* Example: `docker push myrepo/my_app:latest`.

### Delete containers, images, networks and volumes don't use:
```
docker system prune
```
* Cleans up containers, images, networks and volumes don't use.
* Use `-a` to remove all containers, images don't use.


## Dockerfile
[<ins>See More</ins>](DOCKER_FILE.md)

## Docker Compose
[<ins>See More</ins>](DOCKER_COMPOSE.md)