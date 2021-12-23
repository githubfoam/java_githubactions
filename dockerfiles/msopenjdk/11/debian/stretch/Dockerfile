ARG DISTRO
ARG DISTRO_VERSION
FROM $DISTRO:$DISTRO_VERSION

ARG JDK_VER
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
    && apt-get install msopenjdk-$JDK_VER -y \
    #Change the default JDK on Linux
    && update-java-alternatives --set msopenjdk-$JDK_VER-amd64

ENV LANG en_US.UTF-8
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-$JDK_VER-amd64
ENV PATH "${JAVA_HOME}/bin:${PATH}"