FROM ruby

RUN apt-get update && apt-get install -y nodejs sqlite3 yarn gem bundler
RUN gem install rails
RUN gem install bundler:1.16.1
RUN gem install rake

ONBUILD EXPOSE 3000

ONBUILD COPY app /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed