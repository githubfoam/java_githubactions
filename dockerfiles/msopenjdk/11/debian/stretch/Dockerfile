ARG DISTRO
ARG DISTRO_VERSION
FROM $DISTRO:$DISTRO_VERSION

ARG JDK_VER
LABEL org.opencontainers.image.authors="githubfoam"

# https://docs.microsoft.com/en-us/java/openjdk/install
RUN set -eux \
    && apt-get update \
    && apt-get install wget gnupg -y \
    #add the repository
    && wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg \
    && install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/ \
    && wget -q https://packages.microsoft.com/config/debian/9/prod.list -O /etc/apt/sources.list.d/microsoft-prod.list \
    && apt-get install apt-transport-https -y \
    && apt-get update \
    && apt-get install msopenjdk-$JDK_VER -y \
    #Change the default JDK on Linux
    # && update-java-alternatives --set msopenjdk-17-amd64
    && update-java-alternatives --set msopenjdk-$JDK_VER-amd64

ENV LANG en_US.UTF-8
# ENV JAVA_HOME /usr/lib/jvm/msopenjdk-17-amd64
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-$JDK_VER-amd64
ENV PATH "${JAVA_HOME}/bin:${PATH}"