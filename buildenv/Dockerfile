#
# Ubuntu Dockerfile
#
# https://github.com/jterstriep/leam
#

# Pull base image.
FROM ubuntu:14.04

# replace the source list to point to EC2 servers
ADD sources.list /etc/apt/sources.list
#RUN  sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list

# Install software dependencies
RUN \
  apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y build-essential checkinstall && \
  apt-get install -y software-properties-common python-software-properties && \
  apt-get install -y python python-dev python-pip python-virtualenv && \
  apt-get install -y python-gdal && \
  apt-get install -y libexpat1-dev && \
  apt-get install -y grass grass-dev libgdal1-1.10.1-grass && \
  apt-get install -y mpi-default-bin mpi-default-dev && \
  apt-get install -y subversion git zip curl wget && \
  rm -rf /var/lib/apt/lists/*

# there might be a bug with pop and requests.  Updating pip with
# easy_install seems to fix it.  It's probably not needed long term.
RUN \
  easy_install -U pip && \
  pip install requests mechanize

# set environment variables
ENV SHELL /bin/bash
ENV HOME /root

# define working directory
WORKDIR /root

CMD ["bash"]
