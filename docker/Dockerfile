# syntax=docker/dockerfile:1
FROM ubuntu:22.04
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=UTC

RUN mkdir -p /install
WORKDIR /install

COPY groq-devtools_0.9.0_amd64.deb ./

RUN apt update && apt upgrade -y
RUN apt install software-properties-common -y
RUN add-apt-repository ppa:deadsnakes/ppa -y
RUN add-apt-repository -y universe
RUN apt update -y
RUN apt-get -y install git
RUN apt-get -y install wget

RUN apt install ./groq-devtools_0.9.0_amd64.deb -y

RUN apt install -y curl python3.8-distutils
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
RUN python3.8 get-pip.py


RUN python3.8 -m pip install Deprecated==1.2.13 numpy==1.21.2 ansicolors==1.1.8 parse==1.19.0 ordered-set==4.0.2 parsimonious==0.8.1 protobuf==3.19.0

WORKDIR /