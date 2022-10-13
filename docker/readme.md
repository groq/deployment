# Docker Setup for Ubuntu 22.04 and GroqWare Developer Package

For those that would like to install the GroqWare Developer package in a docker container, we’ve provided a dockerfile and some instructions.

## Prerequisites

* Docker Installed and Running. See the [Install Docker](https://docs.docker.com/engine/install/) page for more information.

* GroqWare Developer Package for Ubuntu 22.04 (groq-devtools_0.9.0_amd64.deb).

* Dockerfile included in [this folder](../docker/).

# Build Docker and Run

Ensure you have the GroqWare debian package and the provided dockerfile, then build your docker image:

`docker build -t groq-dev .`

Run the image in interactive mode:

`docker run -it groq-dev`