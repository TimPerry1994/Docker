FROM provisioning_zabbix
MAINTAINER Tim Perry

WORKDIR /opt
RUN apt-get -y update

RUN apt-get install -y zabbix-agent


RUN sed -i '95s/.*/Server=52.211.193.78/g' /etc/zabbix/zabbix_agentd.conf
RUN sed -i '136s/.*/ServerActive=52.211.193.78/g' /etc/zabbix/zabbix_agentd.conf
RUN sed -i '147s/.*/Hostname=zabbix/g' /etc/zabbix/zabbix_agentd.conf

ENTRYPOINT service zabbix-agent restart && bash


EXPOSE 10050
EXPOSE 80
EXPOSE 10051
