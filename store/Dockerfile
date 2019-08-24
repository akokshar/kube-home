FROM ubuntu:rolling

ENV [ LANG=en_US.UTF-8, LANGUAGE=en_US, LC_ALL=en_US.UTF-8 ]

RUN export DEBIAN_FRONTEND=noninteractive && \
  apt update && apt install -y samba avahi-daemon && \
  apt-get autoremove -y && apt-get clean -y && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/apt/*

EXPOSE 137 138 139 445

RUN useradd -M -N --uid 2000 timemachine && \
  useradd -M -N --uid 2001 share
