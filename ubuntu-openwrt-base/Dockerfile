FROM ubuntu:xenial

MAINTAINER Nico Maas <mail@nico-maas.de>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y -qq && \
    apt-get install -y --no-install-recommends git-core subversion mercurial nano sudo wget \
        build-essential libssl-dev libncurses5-dev unzip gawk zlib1g-dev && \

# clean up
    apt-get remove -y openssh-client manpages manpages-dev krb5-locales locales && \
    apt-get autoremove -qqy && \
    apt-get autoclean -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && mkdir /var/lib/apt/lists/partial && \

# add user
    useradd -m openwrt && \
    echo 'openwrt ALL=NOPASSWD: ALL' > /etc/sudoers.d/openwrt

USER openwrt