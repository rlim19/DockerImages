#
# Workspace Dockerfile
#

FROM ubuntu:14.04 
MAINTAINER <rlim.email@gmail.com>

# Install utilities
RUN \
  sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
  apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y build-essential && \
  apt-get install -y language-pack-en && \
  apt-get install -y software-properties-common && \
  apt-get install -y byobu curl git htop man unzip vim wget less htop unzip sudo
  #rm -rf /var/lib/apt/lists/* 

# Python Installation
RUN \
  apt-get install -y libxml2-dev python build-essential make gcc && \
  apt-get install -y python-dev python-pip && \
  apt-get install -y libfreetype6 libfreetype6-dev libxft-dev && \
  apt-get install -y python-imaging libpng-dev && \ 
  apt-get install -y libzmq-dev && \
  apt-get install -y python-numpy python-scipy

RUN \
  pip install -U setuptools &&\
  pip install -U pip &&\
  pip install -U distribute &&\
  pip install pyzmq && \
  pip install matplotlib && \
  pip install pandas && \
  pip install jinja2 && \
  pip install ipython && \
  pip install ipython-cluster-helper && \
  pip install biopython

# add the ipython parallel
RUN pip install "ipython[parallel]"

# Set environment variables.
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# Define working directory.
WORKDIR /root

# Add util files.
ADD root/.bashrc /root/.bashrc
ADD root/.bash_aliases /root/.bash_aliases
ADD root/.gitconfig /root/.gitconfig
ADD root/.scripts /root/.scripts
ADD root/.vimrc /root/.vimrc
ADD root/.vim /root/.vim
ADD root/bin /root/bin

# Define default command.
CMD ["bash"]
