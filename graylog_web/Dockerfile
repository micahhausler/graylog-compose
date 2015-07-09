FROM debian:jessie

MAINTAINER Micah Hausler, micah.hausler@ambition.com

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get -y install \
    curl \
    dnsutils \
    git \
    htop \
    jq \
    less \
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

ADD https://packages.graylog2.org/releases/graylog2-web-interface/graylog-web-interface-1.1.4.tgz /opt/

RUN cd /opt/ \
    && tar xfz graylog-web-interface-1.1.4.tgz \
    && mv graylog-web-interface-1.1.4 graylog \
    && rm graylog-web-interface-1.1.4.tgz

EXPOSE 9443

WORKDIR /opt/graylog
CMD /opt/graylog/bin/graylog-web-interface -Dhttps.port=9443
