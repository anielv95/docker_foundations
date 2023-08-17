# docker_foundations
This repository is a resume for the essential pieces when you're learning Docker

## What is Docker?

The following lists was extracted from docker oficial documentation https://docs.docker.com/get-started/overview/ 

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

!(https://docs.docker.com/assets/images/architecture.svg)
