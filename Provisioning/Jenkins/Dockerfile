FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt/
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | apt-key add -
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
RUN apt-get update
RUN apt-get install -y jenkins



USER root
ENTRYPOINT service jenkins start && bash
EXPOSE 8080
