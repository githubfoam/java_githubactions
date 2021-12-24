ARG DISTRO
ARG DISTRO_VERSION
FROM $DISTRO:$DISTRO_VERSION

ARG JDK_VER
LABEL org.opencontainers.image.authors="githubfoam"

# https://docs.microsoft.com/en-us/java/openjdk/install
RUN set -eux \
    && yum update -y \
    #add the repository    
    &&  rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm \
    && yum update \
    && yum install msopenjdk-$JDK_VER -y
    #Change the default JDK on Linux
    # && update-java-alternatives --set msopenjdk-$version

ENV LANG en_US.UTF-8
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-$vJDK_VER
ENV PATH "${JAVA_HOME}/bin:${PATH}"