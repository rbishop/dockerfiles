FROM rbishop/ruby:base
MAINTAINER Richard Bishop <richard@rubiquity.com>

RUN curl https://s3.amazonaws.com/pkgr-buildpack-ruby/current/ubuntu-14.04/ruby-2.1.3.tgz -o - | sudo tar xzf - -C /usr/local
RUN echo "gem: --no-document" > ~/.gemrc

ENV GEM_HOME /usr/local/lib/ruby/gems/2.1.0
RUN gem install bundler
