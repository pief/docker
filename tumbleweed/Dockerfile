FROM opensuse:tumbleweed
MAINTAINER Pieter Hollants <pieter@hollants.com>

# Get the latest base updates
RUN zypper --non-interactive --gpg-auto-import-keys refresh && zypper --non-interactive update

# When run as a container directly, print number of available updates. This allows
# running a cronjob on the Docker like this:
#
#   [[ $(docker run --rm pief/tumbleweed | tr -d '\r') != "0" ]] && docker build -t pief/tumbleweed --no-cache https://github.com/pief/docker.git#:tumbleweed && docker push pief/tumbleweed
#
# This needs the cron user to have DockerHub credentials stored.
CMD zypper -q lu | wc -l
