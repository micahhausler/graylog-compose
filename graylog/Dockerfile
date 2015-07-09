FROM debian:jessie

MAINTAINER Micah Hausler, micah.hausler@ambition.com

ENV DEBIAN_FRONTEND noninteractive

ENV JAVA_HOME /opt/graylog/embedded/jre

RUN apt-get update && \
    apt-get -y install \
    curl \
    dnsutils \
    git \
    htop \
    jq \
    less \
    lsof \
    man \
    net-tools \
    ntp \
    openjdk-7-jdk \
    pwgen \
    tzdata \
    unzip \
    vim \
    vim-common \
    wget \
    zip \
    && rm -rf /var/lib/apt/lists/*

ADD https://packages.graylog2.org/releases/graylog2-server/graylog-1.1.4.tgz /opt/graylog-1.1.4.tgz

RUN cd /opt/ \
    && tar xfz graylog-1.1.4.tgz \
    && mv graylog-1.1.4/ graylog/ \
    && rm graylog-1.1.4.tgz

VOLUME /var/log/graylog
VOLUME /opt/graylog/plugin

# gelf tcp/udp
EXPOSE 12201
EXPOSE 12201/udp

# rest api
EXPOSE 12900

# syslog
EXPOSE 514
EXPOSE 514/udp

WORKDIR /opt/graylog
CMD java -jar graylog.jar server
