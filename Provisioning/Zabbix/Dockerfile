FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt
RUN wget http://repo.zabbix.com/zabbix/3.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.2-1+trusty_all.deb
RUN dpkg -i zabbix-release_3.2-1+trusty_all.deb
RUN apt-get update

#RUN apt-get install -y zabbix-server-mysql zabbix-web-mysql
#RUN zcat /usr/share/doc/zabbix-server-mysql-3.2.1/create.sql.gz | mysql -uroot -p zabbix


RUN apt-get install -y zabbix-agent
ENTRYPOINT service zabbix-agent start && bash

