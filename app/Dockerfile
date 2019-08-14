FROM ruby:latest

RUN mkdir /app
WORKDIR /app
ADD . /app/

RUN gem install bundler:2.0.1
RUN bundle update --bundler

RUN bundle install
EXPOSE 3000

CMD ["bundle", "exec", "puma"]