FROM ubuntu:14.04

MAINTAINER Richard Bishop <richard@rubiquity.com>

# Update apt, system libraries and get ruby dependencies
RUN apt-get update -y
RUN apt-get install -y \
  build-essential \
  wget \
  curl \
  libyaml-dev \
  libxml2-dev \
  libxslt1-dev \
  zlib1g-dev \
  imagemagick \
  libssl-dev \
  libreadline-dev \
  libgdbm-dev \
  libffi-dev \
  libncurses-dev \
  libpq-dev \
  nodejs \
  bison

# Install Ruby 2.1.5 and ignore gem documentation
RUN curl https://s3.amazonaws.com/pkgr-buildpack-ruby/current/ubuntu-14.04/ruby-2.1.5.tgz -o - | sudo tar xzf - -C /usr/local
RUN echo "gem: --no-document" > ~/.gemrc

# Add Ruby binaries to $PATH
ENV PATH /opt/rubies/ruby-2.1.5/bin:$PATH

# Install common and slow installing gems
RUN gem install bundler
RUN gem install nokogiri -- --use-system-libraries --with-xml2-include=/usr/include/libxml2

# Rails expects Node to be accessible with `node` command
RUN ln -s /usr/bin/nodejs /usr/bin/node
