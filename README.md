# V-lang development container in docker 

This is for setting up and development environment for developing in the awesome V-language using a docker container. You can use the container as a stand-alone container or as a devcontainer in vscode. 

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
 - From repo root, build your docker image by running `docker build . -t v-devcontainer` (you can call it what ever you want instead of `v-devcontainer`)

## 3. Running the docker image

### Run the container

You can run the development docker container from the repo root:

```bash

#!/bin/bash

# start docker container, default maps ${PWD} to /developer/project inside the container. You can use any local path instead of ${PWD}
docker run -d \
  -d \
  -v ${PWD}:/developer/project \
  --name v-devcontainer \
  v-devcontainer

```

### Attach a new bash in to the running container

With docker you do not need ssh. To access the command prompt inside the docker container you need to execute the bash command by:

```bash

docker exec -it v-devcontainer /bin/bash

``` 

When you exit the attached container it will stop. Next time you need to develop you need to start the container again.

### Start the stopped container

```bash

# list all containers including the stopped ones.
docker ps -a

# start a stopped container
docker start v-devcontainer

```

## Stop the docker container

To stop the container from taking resources not developing just stop it using:

```bash

docker stop v-devcontainer

```

## Remove the docker container

Sometimes you want to remove a created container. For example when you want to restart from the beginning again. You remove the image by:

```bash

docker rm v-devcontainer

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
