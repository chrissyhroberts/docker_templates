# docker_templates
Dockerfiles for a variety of purposes

## Background

Docker is a useful tool for creating containerised environments for coding and running scripts in a controlled way. 
It has benefits over using a system terminal because you can control which versions of python and so on are installed.

Dockerfiles can also be shared to other users, which makes it easy to make your programmes more impactful. 


This repo is mostly for my personal use. It contains some dockerfile configurations that can be used as a start point when creating a container. 



## Instructions for use

* Download the `dockerfile` and `docker-compose.yaml` files.
* The `dockerfile` is basically a script which installs the OS, packages, a terminal and any programmes or scripts you will need. If you write this properly it will fully install everything a user needs to work with your software
* The `docker-compose.yaml` file contains settings that explain to Docker how it should interact with the host machine. For a basic installation you may not really need one of these. 

> 


## tensorflow_keras_basic

