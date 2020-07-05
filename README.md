# V container for development in V-language

This is for setting up and development environment for developing in V-language using a docker container. You can use the container as a stand-alone container or as a devcontainer in vscode. 

## The container 

This image contains:
- Debian Buster latest version (will be moved to alpine when supported)
- gcc and clang compilers
- nodejs and npm
- git
- open-ssh client to support github push over ssh
- valgrind
- plus other dependencies

Works both with docker for linux and windows.

## 1. Installing docker

[Here are installation instructions on ubuntu](https://docs.docker.com/engine/install/ubuntu/) but on that page there are instructions for other distributions too.

## 2. Building the docker image
 - cd into `.devcontainer` folder
 - Build your docker image by running `docker build . -t v-devcontainer` (you can call it what ever you want instead of `v-devcontainer`)

## 3. Running the docker image

### Run the container

You can run the docker images by using the following command:

```bash

#!/bin/bash

# start docker container, default maps ${PWD} to /developer/project inside the container. You can use any local path instead of ${PWD}
docker run -d \
  -d \
  -v ${PWD}:/developer/project \
  --name v-devcontainer \
  v-devcontainer

```

### Attach to a running container

Attach to container by:

```bash

docker attach v-devcontainer

``` 

When you exit the attached container it will stop. 

### Start a stopped container

```bash

# list all containers including the stopped ones.
docker ps -a

# start a stopped container
docker start v-devcontainer

```

# Using it as Visual Studio Code devcontainer

Devcontainers in Visual Studio Code is a very powerful way for VSCode users to use develop inside a container that maintains all the dependencies you will need for a project and share that easily with others to be up and running in no time.

## 1. Install Visual Studio Code 

Install Visual Studio Code in your favorite operating system.

## 2. Install Remote Development

Install the extension Remote Development from Microsoft. It has id `ms-vscode-remote.vscode-remote-extensionpack`

## 3. Open in container

Use command `Remote-Containers: Open in remote container`. Wait until VSCode built the container and have fun coding.

[Read more here at Microsoft docs](https://code.visualstudio.com/docs/remote/containers) or the [tutorial here](https://code.visualstudio.com/docs/remote/containers-tutorial)
