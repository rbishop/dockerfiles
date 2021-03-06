FROM debian:wheezy
MAINTAINER Richard Bishop <richard@rubiquity.com>

# Git needs to be installed from wheezy backports
RUN echo deb http://http.debian.net/debian wheezy-backports main >> /etc/apt/sources.list
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get -t wheezy-backports install git-core -y

# Upgrade system libraries and get ruby dependencies
RUN apt-get install -y \
  build-essential \
  wget \
  curl \
  libyaml-dev \
  zlib1g \
  zlib1g-dev \
  imagemagick \
  libssl-dev \
  libreadline-dev \
  libgdbm-dev \
  libffi-dev \
  libncurses-dev \
  libpq-dev \
  libpq5 \
  nodejs \
  bison

# Build libxml2 2.7.8 from source
RUN wget http://xmlsoft.org/sources/libxml2-2.7.8.tar.gz && \
    tar zxf libxml2-2.7.8.tar.gz && \
    cd libxml2-2.7.8 && \
    ./configure --prefix=/usr && \
    make && \
    make install && \
    cd .. && \
    rm -rf libxml2-2.7.8*

# Build libxslt 1.1.26 from source
RUN wget http://xmlsoft.org/sources/libxslt-1.1.26.tar.gz && \
    tar zxf libxslt-1.1.26.tar.gz && \
    cd libxslt-1.1.26 && \
    ./configure --prefix=/usr && \
    make && \
    make install && \
    cd .. && \
    rm -rf libxslt-1.1.26.tar.gz*

# Rails expects Node to be accessible with `node` command
RUN ln -s /usr/bin/nodejs /usr/bin/node
