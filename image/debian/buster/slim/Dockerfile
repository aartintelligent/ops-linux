#
# AARTINTELLIGENT : OPS LINUX
#
# PLEASE DO NOT EDIT IT DIRECTLY.
#
# @see https://github.com/aartintelligent/ops-linux
#
FROM debian:buster-slim

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
gnupg \
gnupg1 \
gnupg2 \
wget \
curl

RUN set -eux; \
rm -rf /etc/apt/sources.list.d/*

ADD docker-entrypoint /

RUN set -eux; \
wget -qO "jq-template" 'https://github.com/docker-library/bashbrew/raw/1da7341a79651d28fbcc3d14b9176593c4231942/scripts/jq-template.awk'; \
mv jq-template /usr/bin/jq-template

RUN set -eux; \
mkdir -p \
/home/debian \
/docker-entrypoint.d; \
chown -R debian:root \
/home/debian \
/docker-entrypoint.d \
/docker-entrypoint; \
chmod +x -R \
/docker-entrypoint.d \
/docker-entrypoint

ENTRYPOINT ["/docker-entrypoint"]

USER debian
