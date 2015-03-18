FROM rbishop/ruby-base
MAINTAINER Richard Bishop <richard@rubiquity.com>

# These variables are used through out this file only
ENV RUBY_VERSION_NUM 2.2.1
ENV RUBY_GEM_DIR 2.2.0

RUN curl https://rvm.io/binaries/debian/7/x86_64/ruby-$RUBY_VERSION_NUM.tar.bz2 -o - | tar jxf - -C /usr/local
RUN echo "gem: --no-document" > ~/.gemrc

# Add Ruby programs to the path
ENV PATH /usr/local/ruby-$RUBY_VERSION_NUM/bin:$PATH

# Set the default installation path for gems
ENV GEM_HOME /usr/local/ruby-$RUBY_VERSION_NUM/lib/ruby/gems/$RUBY_GEM_DIR

# Binaries from RVM contain a symlink from cache to an rvm folder sometimes
RUN rm -rf $GEM_HOME/cache

RUN gem install bundler

# Remove configuration environment variables
RUN unset RUBY_VERSION_NUM RUBY_GEM_DIR
