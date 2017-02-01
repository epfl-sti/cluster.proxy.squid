FROM alpine
MAINTAINER STI-IT Ops <stiitops@groupes.epfl.ch>

RUN apk update && apk add squid wget ca-certificates

# https://github.com/hashicorp/consul-template
ENV CONSUL_TEMPLATE_VERSION 0.18.0
ENV CONSUL_TEMPLATE_SHA256 f7adf1f879389e7f4e881d63ef3b84bce5bc6e073eb7a64940785d32c997bc4b
RUN wget -O /tmp/consul-template.zip "https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.zip" \
    && echo "${CONSUL_TEMPLATE_SHA256}  /tmp/consul-template.zip" | sha256sum -c \
    && unzip /tmp/consul-template.zip -d /usr/local/bin \
    && rm /tmp/consul-template.zip

ADD squid.conf.ctmpl /squid.conf.ctmpl
CMD ["/bin/sh", "-c", \
        "/usr/local/bin/consul-template  \
         -template=/squid.conf.ctmpl:/etc/squid/squid.conf \
         -exec='/usr/sbin/squid -N -d 9' -consul-addr=$IPADDR:8500" ]
