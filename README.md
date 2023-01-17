# docker-tutorial
This is the instruction repository for docker.

## Table of Contents

1. [Docker Basic Commands](#basic-commands)
2. [Docker Composer](#docker-composer)
3. [Dockerfile](#dockerfile)
4. [Private Repository
   - [AWS](#aws-private-repository)
   - [API Documentation](#api-documentation)

## Docker Basic Commands
#### # pull latest version from docker-hub to local environment
    docker pull  radis
#### # pull with specific version
    docker pull radis:4.0
###### *** Note: The full command is: docker pull docker.io/library/redis:4.0.[registryDomain/imageName:tag]. When we connect with docker-hub, we don't need to use docker.io/library/ portion. ***
#### # lists existing images
    docker images
    Example
          REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
          redis        latest    5f2e708d56aa   5 days ago      117MB
          redis        4.0       191c4017dcdd   2 years ago     89.3MB
          my-test-app  1.0 	   2e0a4d16e074	  10 minutes ago    116MB
#### # remove image
      docker rmi 2e0a4d16e074
#### # run command first check locally. If not found then it will pull it from docker-hub and then start it.
  docker run redis:4.0
#### # run with detach mode, define port and container name
    docker run -d -p 7001:6379 --name redis-older redis:4.0
#### # lists container
    docker ps
    Example
        	CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS         PORTS      NAMES
          8154f8444eb8   redis:4.0   "docker-entrypoint.s…"   10 minutes ago   Up 2 minutes   6379/tcp   strange_benz
          2595ae900411   redis       "docker-entrypoint.s…"   14 minutes ago   Up 2 minutes   6379/tcp   silly_ellis
#### # lists container only id
    docker ps -aq
    Example
        2e0a4d16e074
        8154f8444eb8
        2595ae900411
#### # remove docker container
    docker rm 2e0a4d16e074
#### # lists running & stoped container
    docker ps -a
    Example
        	CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS                     PORTS      NAMES
          8154f8444eb8   redis:4.0   "docker-entrypoint.s…"   8 minutes ago    Exited (0) 2 minutes ago              strange_benz
          2595ae900411   redis       "docker-entrypoint.s…"   11 minutes ago   Up 19 seconds              6379/tcp   silly_ellis
#### # container start by id or name
    docker start 8154f8444eb8/redis-older
#### # container stop by id or name
    docker stop 8154f8444eb8/redis-older
#### # container logs by id or name
    docker logs 8154f8444eb8/redis-older
#### # interactive terminal. On interactive terminal type env to show the env details
    docker exec -it redis-older /bin/bash or /bin/sh
    or
    docker exec -it redis-older /bin/bash or /bin/bash
#### # docker network
    docker newtork
#### # create network
    docker network create redis-network
#### # container start using docker-composer.yaml file which create default network name
    docker-compose -f docker_compose.yaml up
#### # container stop and remove the default network
    docker-compose -f docker_compose.yml down
#### # build image using Dockerfile
    docker build -t my-app:1.0 .
##### *** Note: first param: my-app is the image name and also set desire version. second param: Dockerfile location. ***
    
