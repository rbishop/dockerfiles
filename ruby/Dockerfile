FROM rbishop/ruby:base
MAINTAINER Richard Bishop <richard@rubiquity.com>

# Install Ruby 2.1.3 and ignore gem documentation
RUN curl https://s3.amazonaws.com/pkgr-buildpack-ruby/current/ubuntu-14.04/ruby-2.1.3.tgz -o - | sudo tar xzf - -C /usr/local
RUN echo "gem: --no-document" > ~/.gemrc

# Add Ruby binaries to $PATH
# Setup Ruby related environment variables
ENV GEM_HOME /usr/local/lib/ruby/gems/2.1.0
ENV NOKOGIRI_USE_SYSTEM_LIBRARIES 1

# Install bundler and set build options for common gems
RUN gem install bundler
RUN bundle config build.nokogiri --with-xml2-include=/usr/include/libxml2
RUN bundle config build.pg --with-pg-config=/usr/bin/pg_config
RUN bundle config build.pg --with-pg-lib=/usr/lib
RUN bundle config build.pg --with-pg-include=/usr/include/postgresql

# Install common and slow installing gems
RUN gem install nokogiri
RUN gem install pg
