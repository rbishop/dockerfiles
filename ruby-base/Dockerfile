FROM ubuntu:14.04
MAINTAINER Richard Bishop <richard@rubiquity.com>

# Update apt, system libraries and get ruby dependencies
RUN apt-get update -y
RUN apt-get install -y \
  build-essential \
  wget \
  curl \
  libyaml-dev \
  libxslt1.1 \
  libxslt-dev \
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

RUN wget http://xmlsoft.org/sources/libxml2-2.7.8.tar.gz && \
    tar zxf libxml2-2.7.8.tar.gz && \
    cd libxml2-2.7.8 && \
    ./configure --prefix=/usr && \
    make && make install

# Rails expects Node to be accessible with `node` command
RUN ln -s /usr/bin/nodejs /usr/bin/node
