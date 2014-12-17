FROM ubuntu:14.04
MAINTAINER Richard Bishop <richard@rubiquity.com>

# Update apt, system libraries and get ruby dependencies
RUN apt-get update -y
RUN apt-get install -y \
  build-essential \
  wget \
  curl \
  libyaml-dev \
  libxml2 \
  libxml2-dev \
  libxslt-dev \
  zlib1g-dev \
  libiconv-hook-dev \
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

# Rails expects Node to be accessible with `node` command
RUN ln -s /usr/bin/nodejs /usr/bin/node
