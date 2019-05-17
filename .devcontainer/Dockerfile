FROM ruby:2.5.1-stretch

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -yq \
  locales

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en

ARG AWS_REGION=us-east-1
ENV AWS_DEFAULT_REGION $AWS_REGION

ENV BUNDLER_VERSION 1.16.4
ENV RAILS_VERSION 5.2.1
ENV RAILS_ENV development
ENV RAILS_LOG_TO_STDOUT true
ENV DISABLE_SPRING yes
ENV NODEJS_VERSION 8.16.0

RUN mkdir ~/.ssh
RUN touch ~/.ssh/known_hosts
RUN ssh-keyscan -H github.com >> ~/.ssh/known_hosts

RUN printf 'gem: --no-ri --no-rdoc' > ~/.gemrc
RUN gem uninstall -i /usr/local/lib/ruby/gems/2.5.0 bundler
RUN gem install bundler -v=$BUNDLER_VERSION
RUN gem install rails -v=$RAILS_VERSION

RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN apt-get install -yq nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install --no-install-recommends -yq yarn