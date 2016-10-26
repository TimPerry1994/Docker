FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt
RUN wget http://repo.zabbix.com/zabbix/3.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.2-1+trusty_all.deb
RUN dpkg -i zabbix-release_3.2-1+trusty_all.deb
RUN apt-get -y update

RUN apt-get install -y apache2

RUN echo "mysql-server mysql-server/root_password password vagrant" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password vagrant" | debconf-set-selections
RUN apt-get install -y mysql-server

RUN apt-get install -y zabbix-server-mysql zabbix-frontend-php

RUN service mysql start && echo "create database zabbix character set utf8 collate utf8_bin; grant all privileges on zabbix.* to zabbix@localhost identified by 'vagrant';" | mysql -h localhost -P 3306 -u root -pvagrant
RUN service mysql start && zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uroot -pvagrant zabbix

RUN sed -i "115iDBPassword=vagrant" /etc/zabbix/zabbix_server.conf
RUN sed -i "89iDBName=zabbix" /etc/zabbix/zabbix_server.conf
RUN sed -i "81iDBHost=localhost" /etc/zabbix/zabbix_server.conf


RUN sed -i "12iListenPort=10051" /etc/zabbix/zabbix_server.conf
RUN sed -i "912idate.timezone = "Europe/London"" /etc/php5/apache2/php.ini

#EXPOSE 80
#EXPOSE 3306
#EXPOSE 10051

ENTRYPOINT  service mysql start && service zabbix-server start && service apache2 start && bash
