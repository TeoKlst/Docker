FROM debian:10.1
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

ENV TERM=xterm

RUN apt-get update &&\
    apt-get install -y xterm curl openssh-server ca-certificates postfix

RUN curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

RUN apt-get install -y gitlab-ce

RUN sed -i "s/unicorn\['worker_timeout'\] = 60/unicorn\['worker_timeout'\] = 300/g" /etc/gitlab/gitlab.rb

EXPOSE 22 80 443

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && \
           gitlab-ctl reconfigure && tail -f /dev/null


# Docker can be useful to test an application that’s still being developed without polluting your libraries.
# You will have to design a Dockerfile that gets the development version of Gitlab - Community Edition installs it with all the dependencies and the necessary configurations, 
# and launches the application, all as it builds.
# The container will be deemed valid if you can access the web client, create users and interact via GIT with this container (HTTPS and SSH).
# Obviously, you are not allowed to use the official container from Gitlab, it would be a shame...


#How To Run
# docker build -t gitlab-container ./ && docker run -itd --restart=on-failure -p 8080:80 -p 8022:22 -p 8443:443 --privileged gitlab-container
# docker run -it 912b3a6793f0 /bin/sh
# docker run ""

# Thank you for installing GitLab!
# GitLab was unable to detect a valid hostname for your instance.
# Please configure a URL for your GitLab instance by setting `external_url`
# configuration in /etc/gitlab/gitlab.rb file.
# Then, you can start your GitLab instance by running the following command:
# sudo gitlab-ctl reconfigure

# For a comprehensive list of configuration options please see the Omnibus GitLab readme
# https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/README.md
