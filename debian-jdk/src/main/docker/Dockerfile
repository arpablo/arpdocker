FROM debian
MAINTAINER Armin Pfarr <armin.pfarr@gmail.com>

ENV JAVA_VER=8 \
	JAVA_HOME=/usr/java/latest \
	JAVA_VERSION=8u112 \
	BUILD_VERSION=b15 

RUN apt-get update && apt-get -y install curl && \
    curl --fail --silent --location --retry 3 \
        --header "Cookie: oraclelicense=accept-securebackup-cookie; " \
        http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSION-$BUILD_VERSION/jdk-$JAVA_VERSION-linux-x64.tar.gz \
        -o /tmp/jdk-8-linux-x64.tar.gz  && \
    mkdir /usr/java && \
    tar xvf /tmp/jdk-8-linux-x64.tar.gz -C /usr/java && \
    export JAVA_DIR=$(ls -1 -d /usr/java/*) && \
    ln -s $JAVA_DIR /usr/java/latest && \
    ln -s $JAVA_DIR /usr/java/default && \
    update-alternatives --install /usr/bin/java java $JAVA_DIR/bin/java 20000 && \
    update-alternatives --install /usr/bin/javac javac $JAVA_DIR/bin/javac 20000 && \
    update-alternatives --install /usr/bin/jar jar $JAVA_DIR/bin/jar 20000 && \
    rm /tmp/jdk-8-linux-x64.tar.gz
