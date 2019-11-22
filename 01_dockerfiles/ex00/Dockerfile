FROM alpine:latest
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

RUN apk update && \
    apk upgrade && \
    apk add vim

ENTRYPOINT vim

# From an alpine image 
# you’ll add to your container your favorite text editor, vim or emacs, 
# that will launch along with your container.

# $ docker build -t vim .
# $ docker run --rm -ti vim
