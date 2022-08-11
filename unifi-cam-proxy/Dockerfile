ARG BUILD_FROM
#!FROM "ghcr.io/home-assistant/amd64-base:3.15"
FROM python:3.8-alpine3.10
WORKDIR /app

RUN apk add --update gcc libc-dev linux-headers libusb-dev
RUN apk add --update netcat-openbsd 
RUN apk add --update ffmpeg=4.1.6-r0
RUN apk add --update git

COPY . .
RUN pip install .

COPY ./docker/entrypoint.sh /
COPY ./docker/client.pem /

ENTRYPOINT ["/entrypoint.sh"]
CMD ["unifi-cam-proxy"]
