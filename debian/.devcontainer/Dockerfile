ARG DEBIAN_VERSION_NAME=stable

FROM debian:${DEBIAN_VERSION_NAME}-slim

# Your Property
ARG USER=user
ARG USER_ID=1000
ARG GROUP_ID=1000

RUN apt-get update && apt-get install -y --no-install-recommends ruby sudo \
    && apt-get clean && rm -rf /var/lib/apt/lists/* \
    && groupadd -g ${GROUP_ID} ${USER} \
    && useradd -u ${USER_ID} -m -s /bin/bash -g ${USER} -G sudo ${USER} \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER ${USER}

# TMP Docker Volume
VOLUME ["/WORKDIR"]

WORKDIR /WORKDIR