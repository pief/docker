FROM pief/dokuwiki
MAINTAINER Pieter Hollants <pieter@hollants.com>

COPY [ "pwauth.conf", "/etc/apache2/conf-enabled/" ]

RUN apt-get update && \
    apt-get install libapache2-mod-authnz-external libapache2-mod-authz-unixgroup pwauth && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
