FROM debian:10.1
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

ENV TS3SERVER_LICENSE=accept

WORKDIR /home/teamspeak

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y wget bzip2 && \
    wget http://dl.4players.de/ts/releases/3.8.0/teamspeak3-server_linux_amd64-3.8.0.tar.bz2 && \
    tar xfvj teamspeak3-server_linux_amd64-3.8.0.tar.bz2

EXPOSE 9987/udp 10011 30033

WORKDIR teamspeak3-server_linux_amd64

ONBUILD RUN cd teamspeak3-server_linux_amd64 &&\
                /teamspeak3-server_linux_amd64$ ./ts3server_startscript.sh start

ONBUILD RUN /teamspeak3-server_linux_amd64$ ./ts3server_startscript.sh status

ENTRYPOINT sh ts3server_minimal_runscript.sh

# From a debian image you will add the appropriate sources to create a TeamSpeak server, 
# that will launch along with your container.
# It will be deemed valid if at least one user can connect to it and engage in a normal discussion (no far-fetched setup),
# so be sure to create your Dockerfile with the right options.
# Your program should get the sources when it builds, they cannot be in your repository.

# docker build -t teamspeak .
# docker run --rm -p 9987:9987/udp -p 10011:10011 -p 30033:30033 teamspeak