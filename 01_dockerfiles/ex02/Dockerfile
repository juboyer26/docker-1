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

#FROM ft-rails:on-build
#EXPOSE 3000
#CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"] 

# ft-rails:on-build needs to be an existing image first
# 's' is an alias for 'server'
# -b binds an IP address
# -p specifies port

#docker build -t ft-rails:on-build -f ft-rails/Dockerfile .
#docker build -t rails-img .
#docker run -d --name rails-app -it --rm -p 3000:3000 rails-img
