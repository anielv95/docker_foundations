# docker_foundations
This repository is a resume for the essential pieces when you're learning Docker

## What is Docker?

The following lists and images were extracted from docker oficial documentation https://docs.docker.com/get-started/overview/ 

1. It's an open platform for developing, shipping, and running applications
2. It enables you to separate your applications from your infrastructure so you can deliver software quickly
3. It lets you manage your infrastructure in the same way you manage your applications
4. It provides to package and run an application in a loosely isolated environment called a container
5. It provides tooling and a platform to manage the lifecycle of your containers

## Architecture

1. It's a client server architecture
2. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers
3. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon
4. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface
5. Another Docker client is Docker Compose, that lets you work with applications consisting of a set of containers

![image](https://docs.docker.com/assets/images/architecture.svg)

## Pieces

1. Docker daemon.

   It listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.
2. Docker client.

   It is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.
3. Docker desktop.

   Docker Desktop is an easy-to-install application for your Mac, Windows or Linux environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper.
4. Docker registries.

   A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is looks for images on Docker Hub by default. You can even run your own private registry.
When you use the docker pull or docker run commands, Docker pulls the required images from your configured registry. When you use the docker push command, Docker pushes your image to your configured registry.

4. Docker objects

When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects.

   1. Images. 
      
An image is a read-only template with instructions for creating a Docker container. 
      
   2. Containers. 
      
A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.
   
## Installing Docker

https://docs.docker.com/get-docker/

I installed docker engine in a linux virtual machine, my guest Operating System is AntiX 22 and I chose to install it from a list of packages https://docs.docker.com/engine/install/debian/#install-from-a-package. Following that path I needed to know what is my OS architecture so the next command was executed.

      dpkg --print-architecture

The next command is to know the os info in your linux machine

      cat /etc/*release

I found that I didn't have libsystemd0 package so I ran:

      sudo apt-get update
      sudo apt-get install libsystemd0

When I finished to install the packages I executed the next

      sudo docker run hello-world

But the following error was showed

      docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?. See 'docker run --help'.

Then I executed:

      sudo dockerd

And I had:

      failed to start daemon: Devices cgroup isn't mounted

In Docker forum (https://forums.docker.com/t/devices-cgroup-isnt-mounted/29279) I found that the problem was because I was missing the `cgroupfs-mount` package so I ran 

      sudo apt-get install cgroupfs-mount

Then I restarted the Docker service with

      sudo service docker restart

and finally the next line was executed successfully 

      sudo docker run hello-world

# Useful extensions 

## Working interactively inside a container in Visual Studio Code:

1. Remote - Containers ( Useful video: https://www.youtube.com/watch?v=cJbvcH0JNGA)
