FROM php:5.6-apache
MAINTAINER Pieter Hollants <pieter@hollants.com>

ENV DOKUWIKI_VERSION 20150810a

COPY [ "dokuwiki-${DOKUWIKI_VERSION}.tar.gz", "dokuwiki-conf.tar.gz", "/root/" ]

RUN tar --strip-components=1 -C /var/www/html -xzf /root/dokuwiki-${DOKUWIKI_VERSION}.tar.gz && \
    rm /root/dokuwiki-${DOKUWIKI_VERSION}.tar.gz && \
    mkdir -p /var/www/persistent/lib && \
    mv /var/www/html/bin /var/www/bin && \
    mv /var/www/html/conf /var/www/persistent/conf && \
    mv /var/www/html/data /var/www/persistent/data && \
    for LIBSUBDIR in plugins tpl ; do \
        mv /var/www/html/lib/$LIBSUBDIR /var/www/persistent/lib/ && \
        ln -s /var/www/persistent/lib/$LIBSUBDIR /var/www/html/lib/$LIBSUBDIR ; \
    done && \
    tar -C /var/www -xzf /root/dokuwiki-conf.tar.gz && \
    rm /root/dokuwiki-conf.tar.gz && \
    chown www-data /var/www/persistent/conf/local.php* && \
    chown www-data /var/www/persistent/conf/users.auth.php && \
    chown www-data /var/www/persistent/conf/acl.auth.php && \
    chown www-data /var/www/persistent/conf/plugins.local.php* && \
    chown -R www-data /var/www/persistent/data && \
    chown -R www-data /var/www/persistent/lib && \
    rm /var/www/html/install.php

VOLUME [ "/var/www/persistent" ]
