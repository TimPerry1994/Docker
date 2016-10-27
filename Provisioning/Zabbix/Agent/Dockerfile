FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt
RUN wget http://repo.zabbix.com/zabbix/3.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.2-1+trusty_all.deb
RUN dpkg -i zabbix-release_3.2-1+trusty_all.deb
RUN apt-get -y update

RUN groupadd zabbix
RUN useradd -g zabbix zabbix

RUN apt-get install -y zabbix-agent
RUN service zabbix-agent start

RUN sed -i '95s/.*/Server=prozab-serv/' /etc/zabbix/zabbix_agentd.conf
RUN sed -i '136s/.*/ServerActive=prozab-serv/' /etc/zabbix/zabbix_agentd.conf
#RUN sed -i '147s/.*/Hostname=Zabbix server/' /etc/zabbix/zabbix_agentd.conf

EXPOSE 10050
