FROM ruby:2.7

RUN gem install bundler rubocop solargraph ruby-debug-ide

# Install git, process tools
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get update && \
    apt-get -y install git procps nodejs

RUN npm install -g yarn

# Clean up
RUN apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Set the default shell to bash instead of sh
ENV SHELL /bin/bash

WORKDIR /app
