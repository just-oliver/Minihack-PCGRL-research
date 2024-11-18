# -*- mode: dockerfile -*-
FROM nvidia/cuda:11.0.3-devel-ubuntu20.04

ARG PYTHON_VERSION=3.8
ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -yq \
        bison \
        build-essential \
        cmake \
        curl \
        flex \
        git \
        libbz2-dev \
        ninja-build \
        wget

# Set up conda
WORKDIR /opt/conda_setup
RUN curl -o miniconda.sh https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
     chmod +x miniconda.sh && \
     ./miniconda.sh -b -p /opt/conda && \
     /opt/conda/bin/conda install -y python=$PYTHON_VERSION && \
     /opt/conda/bin/conda clean -ya

ENV PATH=/opt/conda/bin:$PATH

# Install Jupyter and development tools
RUN python -m pip install --upgrade pip ipython ipdb && \
    pip install jupyter notebook jupyterlab && \
    mkdir -p ~/.jupyterlab/user-settings/@jupyterlab/apputils-extension/ && \
    echo '{ "theme":"JupyterLab Dark" }' > themes.jupyterlab-settings

# Copy project files
COPY . /opt/minihack/
WORKDIR /opt/minihack
RUN pip install minihack

# Create and switch to workspace directory
WORKDIR /workspace

# Expose Jupyter port
EXPOSE 8888

# Start Jupyter Lab by default
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
