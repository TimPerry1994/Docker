FROM provisioning_java
MAINTAINER Tim Perry

ENV JAVA_HOME="/usr/lib/jvm/java-1.8.0-openjdk-amd64"
USER root
WORKDIR /opt
COPY ./shared/rundeck-2.6.11-1-GA.deb /opt
copy ./shared/rundeck-config.properties /etc/rundeck/
RUN apt-get install openssh-client -y
RUN echo "N" | dpkg -i rundeck-2.6.11-1-GA.deb

ENTRYPOINT service rundeckd start && bash
EXPOSE 4440
EXPOSE 4443
