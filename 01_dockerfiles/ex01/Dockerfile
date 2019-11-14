FROM debian:10.1
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

ENV TERM=xterm

RUN apt-get update

RUN apt-get update && apt-get upgrade -y

RUN wget http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2

RUN tar xfvj teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2

EXPOSE 9987 10011 30033

ONBUILD RUN cd teamspeak3-server_linux_amd64 &&\
    /teamspeak3-server_linux_amd64$ ./ts3server_startscript.sh start

ONBUILD RUN /teamspeak3-server_linux_amd64$ ./ts3server_startscript.sh status


# From a debian image you will add the appropriate sources to create a TeamSpeak server, 
# that will launch along with your container.
# It will be deemed valid if at least one user can connect to it and engage in a normal discussion (no far-fetched setup),
# so be sure to create your Dockerfile with the right options.
# Your program should get the sources when it builds, they cannot be in your repository.
