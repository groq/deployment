# Running GroqWare Developer Package in a Docker Container
For those that would like to install the GroqWare Developer package in a docker container, we’ve provided sample Dockerfiles for supported operating systems.

## Prerequisites
- An X86_64 host that is a Hasewell or later CPU that supports the FC16C instruction.  You can verify by using the following: 

- ```bash
  $grep f16c /proc/cpuinfo
  ```

- Docker installed and running. See the [Install Docker](https://docs.docker.com/engine/install/) page for more information.  

- One of the operating specific Dockerfiles under the docker directory.

- GroqWare Developer Packages (common and devtools) for the operating system of your container.

## Build Docker and Run
Ensure you have the GroqWare debian package in the same location as the provided Dockerfile, then build your docker image:

```bash
$docker build --tag groq-devel-{os}:{sdk_ver} --file Dockerfile.{os} .
```

where:
- os is the operating system (ubuntu or rocky)
- sdk_ver is the version of the sdk (use the full version)
 
The tag name uses the version information associated with the SDK version.  From time to time you may wish to rebuild without caching using the `--no-cache` flag so your docker image is built with the most recent git repo updates.  However, you may wish to save time by first check if any updates are available by running `git pull` from the desired git repo in your docker container before building without caching.

## Running the Docker Container
Run the image in interactive mode:

```bash
$docker run -it -p 8080:8080 -p 8439:8439 -p 8888:8888 groq-devel-{os}:{sdk_ver}
```

This will log you into the container as the "groq" user and activate the groqflow conda environment by default.

The above ports will be forwarded between the container and host correspond to the following:
- Port 8080 - Netron
- Port 8439 - GroqView
- Port 8888 - Jupyter
