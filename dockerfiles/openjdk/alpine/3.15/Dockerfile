FROM alpine:latest
WORKDIR /root/testdir
ADD com /root/testdir/com

RUN apk add openjdk8
ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV PATH $PATH:$JAVA_HOME/bin

RUN javac com/example/HelloWorld.java
CMD ["java", "com.example.HelloWorld"]