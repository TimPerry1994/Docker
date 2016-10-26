FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt
COPY ./Shared/URBANCODE_DEPLOY_6.2.2_EN_EVAL.zip /opt
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y mysql-server libmysql-java unzip
RUN unzip URBANCODE_DEPLOY_6.2.2_EN_EVAL.zip
ENV JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"

RUN service mysql start\
&& mysql -u root -e "create user 'ibm-ucd'@'localhost' identified by 'vagrant';"\
&& mysql -u root -e "create database uDeploy;"\
&& mysql -u root -e "grant all on uDeploy.* to 'ibm-ucd'@'localhost';"\
&& mysql -u root -e "grant all privileges on uDeploy.* to 'ibm-ucd'@'localhost' with grant option;"\
&& mysql -u root -e "flush privileges;"

WORKDIR ibm-ucd-install
RUN echo "nonInteractive=true" >> install.properties
RUN echo "" >> install.properties
RUN echo "database.type=mysql" >> install.properties
RUN echo "server.initial.password=root" >> install.properties
RUN echo "hibernate.connection.url=jdbc:mysql://localhost:3306/UCD" >> install.properties
RUN echo "hibernate.connection.username=admin" >> install.properties
RUN echo "hibernate.connection.password=vagrant" >> install.properties

#RUN cp /usr/share/java/mysql.jar /ibm-ucd-install/lib/ext
#RUN service mysql start &&\
#./install-server.sh <<EOF\
#\n\
#\n\
#EOF

#RUN service mysql start &&\
#./install-server.sh <<EOF\
#\n\
#\n\
#EOF


#ENTRYPOINT service mysql start && /opt/ibm-ucd/bin/server.run

EXPOSE 8443
EXPOSE 8080
