#
# Ubuntu Dockerfile
#
# https://github.com/jterstriep/leam
#

# Pull base image.
FROM leamgroup/runtime

RUN svn export https://github.com/LEAMgroup/gluc/trunk gluc
RUN cd gluc/src; make; cp gluc /usr/local/bin
RUN svn export http://svn.leamgroup.com/desktop/ewg_luc/trunk leam

# set environment variables
ENV SHELL /bin/bash
ENV HOME /root/leam

# define working directory
WORKDIR /root/leam

CMD ["python", "./startup.py", "--help"]
