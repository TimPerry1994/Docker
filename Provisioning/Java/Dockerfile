FROM ubuntu:14.04
MAINTAINER Tim Perry


WORKDIR /opt
RUN sudo apt-get update
RUN sudo apt-get install -y wget
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u112-b15/jdk-8u112-linux-x64.tar.gz
RUN tar -zxvf jdk-8u112-linux-x64.tar.gz
RUN update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_112/bin/java 100
RUN update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_112/bin/javac 100
