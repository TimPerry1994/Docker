FROM provisioning_maven
MAINTAINER Tim Perry

#Edit sources.list for zabbix
RUN sed -i -e '$a# Zabbix Application PPA' /etc/apt/sources.list
RUN sed -i -e '$adeb http://ppa.launchpad.net/tbfr/zabbix/ubuntu precise main' /etc/apt/sources.list
RUN sed -i -e '$adeb-src http://ppa.launchpad.net/tbfr/zabbix/ubuntu precise main' /etc/apt/sources.list

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C407E17D5F76A32B
RUN apt-get update
RUN echo "vagrant" | apt-get install -y zabbix-server-mysql php5-mysql zabbix-frontend-php

WORKDIR /usr/share/zabbix-server-mysql/
RUN gunzip *gz
RUN service mysql start\
&& mysql -u root -e "create user 'zabbix'@'localhost' identified by '';"\
&& mysql -u root -e "create database zabbix;"\
&& mysql -u root -e "grant all privileges on zabbix.* to 'zabbix'@'localhost';"\
&& mysql -u root -e "flush privileges;"\
&& mysql -u zabbix zabbix < schema.sql\
&& mysql -u zabbix zabbix < images.sql\
&& mysql -u zabbix zabbix < data.sql

#RUN zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uroot -p zabbix
#RUN dpkg -l zabbix-server-pgsql
#RUN service zabbix-server start
#RUN service apache2 start

#RUN 
