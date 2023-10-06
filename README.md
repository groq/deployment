# Groq Deployment Tools
This repository includes various scripts and playbooks that can help users with setting up Groq systems and software. 

## Docker
This directory containes instructions and sample Dockerfiles to build containers that contain the GroqWare development suite to test and explore the tools.

The following are included:
- [Dockerfile.ubuntu](https://github.com/groq/deployment/tree/main/docker/) to create an Ubuntu 22.04 docker container with Groq's Developer Package included. 
- [Dockerfile.rocky](https://github.com/groq/deployment/tree/main/docker/) to create a Rocky 8 docker container with Groq's Developer Package included.

**Note:** both of these will require the appropriate Groq developer packages (deb or rpm), which can be requested from Groq's Customer Portal at [support.groq.com](https://support.groq.com).

