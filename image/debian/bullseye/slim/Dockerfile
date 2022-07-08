#
# AARTINTELLIGENT
#
# OPS LINUX
#
# PLEASE DO NOT EDIT IT DIRECTLY.
#
# @see https://github.com/aartintelligent/ops-linux
#
FROM debian:bullseye-slim

ARG UID=1000

RUN set -eux; \
useradd -u ${UID} -g root -d /home/debian -m debian

RUN set -eux; \
apt-get update; \
DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
software-properties-common \
apt-transport-https \
lsb-release \
ca-certificates \
supervisor \
htop \
jq \
gawk \
git \
gnupg \
gnupg1 \
gnupg2 \
wget \
curl

RUN set -eux; \
rm -rf /etc/apt/sources.list.d/*

ADD docker-debian-entrypoint /

ADD jq-template /usr/bin/jq-template

RUN set -eux; \
mkdir -p \
/home/debian \
/docker-entrypoint.d; \
chown -R debian:root \
/home/debian \
/docker-entrypoint.d \
/docker-debian-entrypoint \
/usr/bin; \
chmod +x -R \
/docker-entrypoint.d \
/docker-debian-entrypoint \
/usr/bin

ENTRYPOINT ["/docker-debian-entrypoint"]

USER debian
