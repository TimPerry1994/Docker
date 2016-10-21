FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt/
VOLUME ~/Docker/Provisioning/Jira/shared:/tmp/shared
RUN wget https://www.atlassian.com/software/jira/downloads/binary/atlassian-jira-software-7.2.3-x64.bin
RUN chmod a+x atlassian-jira-software-7.2.3-x64.bin
RUN (echo "o"; echo "2"; echo "/opt/atlassian/jira"; echo "/var/atlassian/application-data/jira"; echo "2"; echo "8082"; echo "8008"; echo "y"; echo "i"; echo "y") | sudo /opt/atlassian-jira-software-7.2.3-x64.bin
ENTRYPOINT sudo service jira start && bash 

EXPOSE 8082
EXPOSE 8008
