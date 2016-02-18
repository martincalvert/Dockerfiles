FROM alpine:latest

MAINTAINER Martin Calvert 'Martinlcalvert@gmail.com'

RUN apk update && apk add curl zip \
    && curl 'https://releases.hashicorp.com/consul/0.6.3/consul_0.6.3_linux_amd64.zip' > consul.zip \
    && unzip consul.zip \
    && mv consul bin/consul \
    && rm consul.zip \
    && apk del curl zip

EXPOSE 8500

CMD consul agent -server -data-dir /tmp/consul
