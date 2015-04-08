FROM ubuntu:14.04
MAINTAINER Traun Leyden <traun.leyden@gmail.com>

# A docker container with the Nvidia kernel module and CUDA drivers installed

ENV CUDA_DEB_URL http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/cuda-repo-ubuntu1404_7.0-28_amd64.deb
ENV CUDA_DEB cuda-repo-ubuntu1404_7.0-28_amd64.deb

RUN apt-get update && apt-get install -q -y \
  wget \
  build-essential

RUN wget $CUDA_DEB_URL

RUN sudo dpkg -i $CUDA_DEB

RUN rm $CUDA_DEB

RUN apt-get update && apt-get install -q -y cuda

# Ensure the CUDA libs and binaries are in the correct environment variables
ENV LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
ENV PATH=$PATH:/usr/local/cuda/bin
