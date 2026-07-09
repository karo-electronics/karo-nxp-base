# Choose the base distro based on the supported ones for the used yocto version. E.g. ubuntu-24.04 for scarthgap.
ARG BASE_DISTRO=ubuntu-24.04

FROM crops/yocto:${BASE_DISTRO}-base

USER root

RUN apt-get update && apt-get install -y --no-install-recommends \
    parted \
    mtools \
    repo \
    minicom \
    dfu-util \
    uuu \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install --break-system-packages oelint-adv

RUN userdel -r ubuntu; usermod -u 1000 yoctouser; groupmod -g 1000 yoctouser
RUN chsh -s /bin/bash yoctouser

RUN mkdir /yocto-shared
RUN chown -R 1000:1000 /yocto-shared

USER yoctouser