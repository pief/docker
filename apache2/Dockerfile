FROM pief/tumbleweed
MAINTAINER Pieter Hollants <pieter@hollants.com>

RUN mkdir /tmp/rpms ; \
    zypper --non-interactive --pkg-cache-dir /tmp/rpms download aaa_base \
                                                                apache2 \
                                                                apache2-prefork \
                                                                libapr1 \
                                                                libapr-util1 ; \
    find /tmp/rpms -name *.rpm -exec rpm -i --nodeps {} \; ; \
    rm -rf /tmp/rpms ; \
    zypper clean -a

EXPOSE 80

CMD [ "/usr/sbin/httpd", "-D", "FOREGROUND" ]
