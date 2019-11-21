FROM alpine:latest
LABEL Teo Kelestura (tkelest@student.wethinkcode.co.za)

RUN apk update && \
    apk upgrade && \
    apk add emacs

ENTRYPOINT emacs

# From an alpine image 
# you’ll add to your container your favorite text editor, vim or emacs, 
# that will launch along with your container.

# $ docker build -t myalpineimage:latest .
# $ docker build -t ex00 .
# docker run --rm -ti ex00
