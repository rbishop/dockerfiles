FROM ubuntu:14.04

MAINTAINER Richard Bishop <richard@rubiquity.com>

# Update apt, system libraries and get ruby dependencies
RUN apt-get update -y
RUN apt-get install -y \
  build-essential \
  git \
  git-core \
  wget \
  curl \
  libyaml-dev \
  libxml2-dev \
  libxslt1-dev \
  zlib1g-dev \
  imagemagick \
  graphicsmagick \
  libssl-dev \
  libreadline-dev \
  libgdbm-dev \
  libffi-dev \
  nodejs \
  libncurses-dev \
  libsqlite3-dev \
  libmysqlclient-dev \
  libpq-dev \
  bison

# Install ruby-install
RUN cd /tmp &&\
  wget -O ruby-install-0.5.0.tar.gz https://github.com/postmodern/ruby-install/archive/v0.5.0.tar.gz &&\
  tar -xzvf ruby-install-0.5.0.tar.gz &&\
  cd ruby-install-0.5.0/ &&\
  sudo make install

# Install Ruby 2.1.3 and ignore gem documentation
RUN ruby-install ruby 2.1.3 -- --disable-install-rdoc
RUN echo "gem: --no-document" > ~/.gemrc

# Add Ruby binaries to $PATH
ENV PATH /opt/rubies/ruby-2.1.3/bin:$PATH

# Install common and slow installing gems
RUN gem install bundler
RUN gem install nokogiri -- --use-system-libraries --with-xml2-include=/usr/include/libxml2

# Rails expects Node to be accessible with `node` command
RUN ln -s /usr/bin/nodejs /usr/bin/node
