ARG TAG="18.04"
FROM ubuntu:$TAG
ARG version=17
LABEL org.opencontainers.image.authors="githubfoam"

# https://docs.microsoft.com/en-us/java/openjdk/install#change-the-default-jdk-on-linux
RUN set -eux \
    && apt-get update \
    && apt-get install wget lsb-release -y \
    #add the repository
    && ubuntu_release=`lsb_release -rs` \
    && wget https://packages.microsoft.com/config/ubuntu/${ubuntu_release}/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && apt-get install apt-transport-https -y \
    && apt-get update -y \
    && apt-get install msopenjdk-$version -y \
    #Change the default JDK on Linux
    && update-java-alternatives --set msopenjdk-$version-amd64

ENV LANG en_US.UTF-8
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-$version-amd64
ENV PATH "${JAVA_HOME}/bin:${PATH}"