# You are going to create your first Dockerfile to containerize Rails applications. 
# That’s a special configuration: this particular Dockerfile will be generic, and called in another
# Dockerfile, that will look something like this:
# FROM ft-rails:on-build
# EXPOSE 3000
# CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]
# Your generic container should install, via a ruby container, all the necessary dependencies and gems, then copy your rails application in the /opt/app folder of your
# container. Docker has to install the approtiate gems when it builds, but also launch
# the migrations and the db population for your application. The child Dockerfile should
# launch the rails server (see example below). If you don’t know what commands to use,
# it’s high time to look at the Ruby on Rails documentation.

# ONBUILD ADD . /app/src
# ONBUILD RUN /usr/local/bin/python-build --dir /app/src

# FROM ruby

# RUN apt-get update && \
#     apt-get install nodejs -y && \
#     gem install rails && \
#     mkdir -p /opt/app

# ONBUILD WORKDIR /opt/app
# ONBUILD ADD railsapp /opt/app

# ONBUILD RUN bundle install && rake db:migrate && rake db:seed

# mkdir -p https://superuser.com/questions/165157/what-does-the-p-flag-do-in-mkdir-p

# https://hub.docker.com/_/rails/
# https://www.freecodecamp.org/news/painless-rails-development-environment-setup-with-docker/
#  FYI https://serverfault.com/questions/644180/what-does-qq-argument-for-apt-get-mean
# rake db:setup https://blog.cloud66.com/migrating-a-rails-application-to-docker/
# http://www.xyzpub.com/en/ruby-on-rails/3.2/seed_rb.html
# rake db:migrate https://medium.com/@tushartuteja/setting-up-rails-with-postgres-using-docker-426c853e8590

# name ft-rails
FROM                        ruby:latest
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

RUN                            gem install rails sqlite3 &&\
                                apt update &&\
                                apt install nodejs -y

ONBUILD ADD            app /opt/app

ONBUILD WORKDIR    /opt/app

ONBUILD EXPOSE    3000

ONBUILD RUN            bundle install &&\
                                bundle exec rake db:migrate &&\
                                bundle exec rake db:seed

# cd ft-rails && docker build . -t ft-rails:on-build && cd ..
# docker build . -t example
# docker run -it -p 3000:3000 example