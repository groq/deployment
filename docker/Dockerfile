FROM ubuntu:22.04
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=UTC

##############################################################################
######## Install the GroqWare Suite Developer Package ########################
##############################################################################

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        wget \
        ca-certificates \
        build-essential \
        gcc-10 \
        libstdc++-10-dev \
        libssl-dev \
        cmake \
        libgmpxx4ldbl \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        software-properties-common \
        gpg-agent \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
    && add-apt-repository ppa:deadsnakes/ppa -y

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3.10 \
        python3.10-dev \
    && rm -rf /var/lib/apt/lists/*

ARG GROQ=0.10.0

COPY groq-common_${GROQ}_amd64.deb /tmp/groq-common.deb

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        /tmp/groq-common.deb \
    && rm -rf /var/lib/apt/lists/*

RUN rm /tmp/groq-common.deb

COPY groq-devtools_${GROQ}_amd64.deb /tmp/groq-devtools.deb

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        /tmp/groq-devtools.deb \
    && rm -rf /var/lib/apt/lists/*

RUN rm /tmp/groq-devtools.deb

##############################################################################
######## Install Miniconda and Create a GroqFlow Conda Environment ###########
##############################################################################

RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh

RUN bash /tmp/miniconda.sh -b

ARG CONDA_PATH=/root/miniconda3/condabin
RUN $CONDA_PATH/conda init
RUN $CONDA_PATH/conda config --set auto_activate_base False
RUN $CONDA_PATH/conda create -n groqflow python=3.10
RUN echo "conda activate groqflow" >> ~/.bashrc
RUN $CONDA_PATH/conda run -n groqflow pip install --upgrade pip

RUN rm /tmp/miniconda.sh

##############################################################################
######## Git Clone the GroqFlow and GroqAPI Repositories #####################
########     and Install Their Dependancies              #####################
##############################################################################

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
    && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/groq/groqflow.git
RUN git clone https://github.com/groq/GroqAPI.git

RUN $CONDA_PATH/conda run -n groqflow pip install -e /groqflow

##############################################################################
######## Install Netron to visualize ONNX model files ########################
##############################################################################

RUN $CONDA_PATH/conda run -n groqflow pip install netron
