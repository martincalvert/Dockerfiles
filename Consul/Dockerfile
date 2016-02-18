FROM alpine:latest

MAINTAINER Martin Calvert 'Martinlcalvert@gmail.com'

RUN apk update && apk add curl zip \
    && curl 'https://releases.hashicorp.com/consul/0.6.3/consul_0.6.3_linux_amd64.zip' > consul.zip \
    && unzip consul.zip \
    && mv consul bin/consul \
    && rm consul.zip \
    && mkdir consul consul/data consul/ui \
    && curl 'https://releases.hashicorp.com/consul/0.6.3/consul_0.6.3_web_ui.zip' > consul_ui.zip \
    && unzip -d consul/ui consul_ui.zip \
    && rm consul_ui.zip \
    && apk del curl zip

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 8600 8600/udp
ENV DNS_RESOLVES consul
ENV DNS_PORT 8600

ADD ./consul.json /config/
ENTRYPOINT ["/bin/consul", "agent", "-server", "-config-dir=/config/"]
