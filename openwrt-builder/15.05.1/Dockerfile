FROM nmaas87/ubuntu-openwrt-base:latest as BUILD
MAINTAINER Nico Maas <mail@nico-maas.de>
ENV DEBIAN_FRONTEND noninteractive
USER openwrt
RUN date && \
    cd ~ && git clone --depth=1 -b chaos_calmer git://github.com/openwrt/openwrt.git && \
    cd openwrt && \
    ./scripts/feeds update -a && \
    ./scripts/feeds install -a && \
    echo CONFIG_TARGET_brcm2708=y > .config && \
    echo CONFIG_TARGET_brcm2708_bcm2708=y >> .config && \
    make defconfig && \
    echo CONFIG_TARGET_ROOTFS_TARGZ=y >> .config && \
    make prereq && \
    make -j1 V=s && \
    date && \
    echo CONFIG_TARGET_brcm2708=y > .config && \
    echo CONFIG_TARGET_brcm2708_bcm2709=y >> .config && \
    make defconfig && \
    echo CONFIG_TARGET_ROOTFS_TARGZ=y >> .config && \
    make prereq && \
    make -j1 V=s && \
    date
#CMD ["/bin/bash"]

FROM scratch
MAINTAINER Nico Maas <mail@nico-maas.de>
COPY --from=BUILD /home/openwrt/openwrt/bin/brcm2708 /
