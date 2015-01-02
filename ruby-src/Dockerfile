FROM rbishop/ruby-base
MAINTAINER Richard Bishop <richard@rubiquity.com>

# This is for installing Ruby from source when a prebuilt binary is not available yet

# Use ruby-install to install Ruby
RUN wget -O ruby-install-0.5.0.tar.gz https://github.com/postmodern/ruby-install/archive/v0.5.0.tar.gz && \
    tar -xzvf ruby-install-0.5.0.tar.gz && \
    cd /ruby-install-0.5.0 && \
    make install && \
    cd / && \
    ruby-install -j4 -i /usr/local/ruby-2.2.0 ruby 2.2.0 && \
    rm -rf ruby-install* && \
    rm -rf /usr/local/share/ruby-install && \
    rm -rf /usr/local/src

# Configure PATH and Ruby specific settings
ENV PATH /usr/local/ruby-2.2.0/bin:$PATH
ENV GEM_HOME /usr/local/ruby-2.2.0/lib/ruby/gems/2.2.0
RUN echo "gem: --no-document" > ~/.gemrc
RUN gem install bundler
