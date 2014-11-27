FROM rbishop/ruby:base

MAINTAINER Richard Bishop <richard@rubiquity.com>

# Install Ruby 2.1.3 and ignore gem documentation
RUN curl https://s3.amazonaws.com/pkgr-buildpack-ruby/current/ubuntu-14.04/ruby-2.1.3.tgz -o - | sudo tar xzf - -C /usr/local
RUN echo "gem: --no-document" > ~/.gemrc

# Add Ruby binaries to $PATH
ENV PATH /opt/rubies/ruby-2.1.3/bin:$PATH

# Install common and slow installing gems
RUN gem install bundler
RUN gem install nokogiri -- --use-system-libraries --with-xml2-include=/usr/include/libxml2

# Rails expects Node to be accessible with `node` command
RUN ln -s /usr/bin/nodejs /usr/bin/node
