# docker_templates
Dockerfiles for a variety of purposes

## Background

Docker is a useful tool for creating containerised environments for coding and running scripts in a controlled way. 
It has benefits over using a system terminal because you can control which versions of python and so on are installed.

Dockerfiles can also be shared to other users, which makes it easy to make your programmes more impactful. 


This repo is mostly for my personal use. It contains some dockerfile configurations that can be used as a start point when creating a container. 



## Instructions for use
* Make sure that you've installed [docker](https://docs.docker.com/)
* Download the `dockerfile` and `docker-compose.yaml` files and save them in a folder on your host system (let's say 
  * The `dockerfile` is basically a script which installs the OS, packages, a terminal and any programmes or scripts you will need. If you write this properly it will fully install everything a user needs to work with your software
  * The `docker-compose.yaml` file contains settings that explain to Docker how it should interact with the host machine. For a basic installation you may not really need one of these. 

## Build the Docker Image
To build a Docker image from your Dockerfile, you use the docker build command. You need to run this command from the directory where your Dockerfile is located. Optionally, you can tag your image using the -t flag to give it a name and optionally a tag in the format name:tag.

`docker build -t image001:latest .`

Here, `-t image001:latest` tags your image as image001 with the `latest` tag. 
The `.` at the end of the command tells Docker to use the current directory as the context for the build.

You can list the existing images

`docker images`

## Make a Docker Container
After building the image, you can create a container based on that image. To do this, use the docker run command:

`docker run -it --name container001 image001:latest`

Here’s what the options mean:
`-it` allows you to interact with the container via your terminal.  
`--name container001` names your container `container001`.  
`image001:latest` specifies the image to use.  
If your application listens on a port (for example, a web server), you might need to map the ports using the -p option, like so:  
`docker run -it -p 5000:5000 --name container001 image001:latest`  
This command maps port 5000 on your host to port 5000 on your Docker container, which is typical for web applications.  

If you want to share a folder with the 
`docker run --name container001 -it -v /Users/icrucrob/Documents/Docker/test/app:/app image001:latest`
Here `-v /Users/icrucrob/Documents/Docker/test/app:/app` provides the `host:container` folders to share.

If you want to specify RAM and CPU
`docker run -it --memory="4g" --cpus="2" your_image_name`

My recommendation is the following for an M3 processor on a mac silicon
`docker run --memory="32g" --cpus="12" --name container001 -it -v /Users/icrucrob/Documents/Docker/test/app:/app image001:latest`


Type exit to quit the container

## Show existing containers
`docker ps -a`

## Start and connect to existing container with interactive shell

If you want to connect to a docker container and don't mind the container stopping when you close the shell by typing `exit`
```
docker start container001
docker attach container001
```

If you want to connect to a docker container and want the container to keep running when you close the shell by typing `exit`
```
docker start container001
docker exec -it container001 /bin/zsh
```

## Deleting images
`docker images` shows the list of images
`docker rmi [image_id_or_name]` removes the image
`docker rmi [image:tag]` removes a specific version

## Deleting containers
`docker ps -a` lists all containers
`docker rm [container]` removes the container
 
## NOTE
For doing stuff with AI on Docker, you'll probably need to look at the `preferences/resources` settings on Docker Desktop. This needs a fair whack of resources. 


## Install CVAT
https://docs.cvat.ai/docs/administration/basics/installation/
