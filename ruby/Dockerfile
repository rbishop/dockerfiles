FROM rbishop/ruby-base
MAINTAINER Richard Bishop <richard@rubiquity.com>

RUN mkdir /usr/local/ruby-2.1.5
RUN curl https://s3.amazonaws.com/pkgr-buildpack-ruby/current/debian-7/ruby-2.1.5.tgz -o - | tar xzf - -C /usr/local/ruby-2.1.5
RUN echo "gem: --no-document" > ~/.gemrc

ENV PATH /usr/local/ruby-2.1.5/bin:$PATH
ENV GEM_HOME /usr/local/ruby-2.1.5/lib/ruby/gems/2.1.0
RUN gem install bundler
