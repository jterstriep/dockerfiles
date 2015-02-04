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

# Install.
RUN \
  apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y gdal-bin grass libgdal1-1.10.1-grass && \
  rm -rf /var/lib/apt/lists/*

#  apt-get install -y python python-pip python-gdal && \
#  apt-get install -y mpi-default-bin && \
#  apt-get install -y subversion git zip curl wget && \

# there might be a bug with pop and requests.  Updating pip with
# easy_install seems to fix it.  It's probably not needed long term.
RUN \
  easy_install -U pip && \
  pip install requests mechanize

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# set environment variables
ENV HOME /root

# define working directory
WORKDIR /root

CMD ["bash"]
