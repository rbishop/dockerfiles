FROM rbishop/ruby:base
MAINTAINER Richard Bishop <richard@rubiquity.com>

# Install Ruby 2.1.3 and ignore gem documentation
RUN curl https://s3.amazonaws.com/pkgr-buildpack-ruby/current/ubuntu-14.04/ruby-2.1.3.tgz -o - | sudo tar xzf - -C /usr/local
RUN echo "gem: --no-document" > ~/.gemrc
ENV GEM_HOME /usr/local/lib/ruby/gems/2.1.0

# Install bundler and set build options for common gems
RUN gem install bundler
RUN bundle config build.nokogiri --use-system-libraries
RUN bundle config build.pg --with-pg-config=/usr/bin/pg_config --with-pg-lib=/usr/lib --with-pg-include=/usr/include/postgresql
