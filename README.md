# Docker + Node.js

Dockerize a Node.js app. 

Watch the full [Docker video](https://youtu.be/gAkwW2tuIqE) on YouTube or read the [Docker Tutorial](https://fireship.io/lessons/docker-basics-tutorial-nodejs/) on Fireship.io. 

# My own Note
## Basic Concept
(from Fireship)

1. Dockerfile: blueprint for building image. It specify the environment and startup action
2. Image: template for running container, or an executable archive, which can be transfered to other place like docker hub
3. Container: running process, application

# Dockerfile explaination
each instruction is considered as 1 step or layer. for the sake of performance, each layer is cached so only the following layers rebuild once any layer made changes. Thus we `COPY` the package specification, and run `npm install` before we move all the other source code since the dependencies seldom change.

### avoid copying unused file
add a `.dockerignore` file and name the unwanted file or folder.

### EXEC form
the last step `CMD` pass argument in array form. it doesn't start a shell session. It is usually the command to start the application


# Container
the format for port mapping of `docker run` is in `local:container`.
just like running process, any change during its lifetime is stored as volatile memory. Stopping the process(container) means the data will loss.


# Volumes
place to store persistant data of the container, like HDD, and it is in the form of folder.
For windows, it stores in the WSL. use `docker volume inspect` to see the location