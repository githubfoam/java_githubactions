FROM debian:stretch-slim
# ARG version=17

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
    && apt-get install msopenjdk-17 -y \
    #Change the default JDK on Linux
    && update-java-alternatives --set msopenjdk-17-amd64

ENV LANG en_US.UTF-8
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-17-amd64
ENV PATH "${JAVA_HOME}/bin:${PATH}"