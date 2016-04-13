# See https://hub.docker.com/r/opensuse/amd64/
#FROM opensuse:tumbleweed
FROM opensuse/amd64:tumbleweed
MAINTAINER Pieter Hollants <pieter@hollants.com>

# Get the latest base updates
RUN zypper --non-interactive --gpg-auto-import-keys refresh && \
    zypper --non-interactive update && \
    zypper clean -a && \
    find /usr/share/locale -name *.mo -exec rm {} \; && \
    rm /var/log/*.log

# When run as a container directly, print number of available updates. This allows
# running a cronjob on the Docker host like this:
#
#   [[ $(docker run --rm pief/tumbleweed | tr -d '\r') != "0" ]] && docker build -t pief/tumbleweed --no-cache https://github.com/pief/docker.git#:tumbleweed && docker push pief/tumbleweed
#
# This needs the cron user to have DockerHub credentials stored.
CMD zypper -q lu | wc -l
