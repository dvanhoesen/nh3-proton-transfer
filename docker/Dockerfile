FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    build-essential \
    gfortran \
    git \
    cmake \
    ninja-build \
    python3 \
    python3-venv \
    python3-pip \
    wget \
    curl \
    ca-certificates \
    bzip2 \
    xz-utils \
    unzip \
    patch \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /opt

RUN git clone --recursive \
    --branch support/v2026.2 \
    --depth 1 \
    https://github.com/cp2k/cp2k.git /opt/cp2k

WORKDIR /opt/cp2k

RUN ./make_cp2k.sh \
    -bd \
    -df all \
    -ef fftw3 \
    -ef libint2 \
    -ef libxc \
    -ef plumed

ENV PATH="/opt/cp2k/install/bin:/opt/cp2k/spack/spack/opt/spack/view/bin:${PATH}"
ENV LD_LIBRARY_PATH="/opt/cp2k/install/lib:/opt/cp2k/spack/spack/opt/spack/view/lib"
