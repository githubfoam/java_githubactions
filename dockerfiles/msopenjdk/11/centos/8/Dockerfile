FROM centos:8
ARG version=17

# https://docs.microsoft.com/en-us/java/openjdk/install
RUN set -eux \
    && yum update -y \
    #add the repository    
    &&  rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm \
    && yum update \
    && yum install msopenjdk-$version -y \
    #Change the default JDK on Linux
    # && update-java-alternatives --set msopenjdk-$version
    && ls -lai /usr/lib/jvm/

ENV LANG en_US.UTF-8
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-$version
ENV PATH "${JAVA_HOME}/bin:${PATH}"