# Docker Setup for Ubuntu 22.04 and GroqWare Developer Package

For those that would like to install the GroqWare Developer package in a docker container, we’ve provided a Dockerfile and some instructions.

## Prerequisites

* Docker Installed and Running on an x86_64 host. See the [Install Docker](https://docs.docker.com/engine/install/) page for more information.

* Dockerfile included in [this folder](../docker/).

* GroqWare Developer Package for Ubuntu 22.04 (groq-devtools_0.9.1_amd64.deb).

# Build Docker and Run

Ensure you have the GroqWare debian package in the same location as the provided Dockerfile, then build your docker image:

`docker build -t groq-devel .`

Run the image in interactive mode:

`docker run -it -p 8080:8080 -p 8439:8439 -p 8888:8888 groq-devel`

The above ports forwarded between the container and host correspond to the following:
* Port 8080 - Netron
* Port 8439 - GroqView
* Port 8888 - Jupyter
