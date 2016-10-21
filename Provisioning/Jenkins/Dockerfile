FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt/
RUN wget wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
RUN sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
RUN sudo apt-get update
RUN sudo apt-get install -y jenkins



USER root
ENTRYPOINT service jenkins start && bash
EXPOSE 8080
