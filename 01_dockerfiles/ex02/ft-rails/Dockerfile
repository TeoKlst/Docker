FROM            ruby:latest
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

RUN             gem install rails sqlite3 &&\
                apt update &&\
                apt install nodejs -y

ONBUILD ADD     app /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD EXPOSE  3000

ONBUILD RUN     bundle install && \
                bundle exec rake db:migrate &&\
 				bundle exec rake db:seed

# You are going to create your first Dockerfile to containerize Rails applications. 
# That’s a special configuration: this particular Dockerfile will be generic, and called in another
# Dockerfile, that will look something like this:
# FROM ft-rails:on-build
# EXPOSE 3000
# CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]
# Your generic container should install, via a ruby container, all the necessary dependencies and gems,
# then copy your rails application in the /opt/app folder of your container.
# Docker has to install the approtiate gems when it builds, but also launch the migrations and the db population for your application.
# The child Dockerfile should launch the rails server (see example below).
# If you don’t know what commands to use, it’s high time to look at the Ruby on Rails documentation.
