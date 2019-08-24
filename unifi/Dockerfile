FROM ubuntu

ENV [ LANG=en_US.UTF-8, LANGUAGE=en_US, LC_ALL=en_US.UTF-8 ]

RUN export DEBIAN_FRONTEND=noninteractive && \
  apt update && apt install -y gnupg && \
  echo "deb http://www.ui.com/downloads/unifi/debian stable ubiquiti" | tee /etc/apt/sources.list.d/ubnt-unifi.list && \
  apt-key adv --keyserver keyserver.ubuntu.com --recv 06E85760C0A52C50 && \
  echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.4.list && \
  apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv BC711F9BA15703C6 && \
  apt-get update && \
  apt-get install -y locales openjdk-8-jre-headless unifi && \
  locale-gen en_US.UTF-8 && locale && \
  apt-get autoremove -y && apt-get clean -y && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/apt/*

WORKDIR /usr/lib/unifi
VOLUME [ "/usr/lib/unifi/data", "/usr/lib/unifi/logs" ]
EXPOSE 8080/tcp 8443/tcp 8880/tcp 8843/tcp 6789/tcp 3478/udp

CMD ["java", "-Xms1024m", "-Xmx1024m", "-Dfile.encoding=UTF-8", "-jar", "/usr/lib/unifi/lib/ace.jar", "start" ]
