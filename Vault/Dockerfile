FROM alpine:latest

MAINTAINER Martin Calvert 'martinlcalvert@gmail.com'

RUN apk update && apk add curl zip \
    && curl 'https://releases.hashicorp.com/vault/0.5.0/vault_0.5.0_linux_amd64.zip' > vault.zip \
    && unzip vault.zip \
    && mv vault bin/vault \
    && rm vault.zip \
    && apk del curl zip
