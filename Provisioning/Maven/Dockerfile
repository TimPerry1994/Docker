FROM provisioning_java
MAINTAINER Tim Perry

#Install maven from .tar.gz file, update-alternatives to enable use of mvn command
WORKDIR /opt
RUN apt-get update
RUN wget http://mirrors.ukfast.co.uk/sites/ftp.apache.org/maven/maven-3/3.3.9/source/apache-maven-3.3.9-src.tar.gz
RUN tar -zxvf apache-maven-3.3.9-src.tar.gz
RUN update-alternatives --install /usr/bin/mvn mvn /opt/apache-maven-3.3.9/apache-maven/src/bin/mvn 100
