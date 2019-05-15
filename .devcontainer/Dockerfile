FROM ruby:2.5.1-stretch

ENV BUNDLER_VERSION 1.16.4
ENV RAILS_VERSION 5.2.3
ENV RAILS_ENV development

RUN gem uninstall -i /usr/local/lib/ruby/gems/2.5.0 bundler
RUN gem install bundler -v=$BUNDLER_VERSION
RUN gem install rails -v=$RAILS_VERSION