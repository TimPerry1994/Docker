FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt
COPY ./Shared/URBANCODE_DEPLOY_6.2.2_EN_EVAL.zip /opt
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y mysql-server libmysql-java unzip
RUN unzip URBANCODE_DEPLOY_6.2.2_EN_EVAL.zip
ENV JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"

RUN service mysql start\
&& mysql -u root -e "create user 'admin'@'localhost' identified by 'vagrant';"\
&& mysql -u root -e "create database uDeploy;"\
&& mysql -u root -e "grant all on uDeploy.* to 'admin'@'localhost';"\
&& mysql -u root -e "grant all privileges on uDeploy.* to 'admin'@'localhost' with grant option;"\
&& mysql -u root -e "flush privileges;"

WORKDIR ibm-ucd-install
RUN echo "nonInteractive=true" >> install.properties
RUN echo "" >> install.properties
RUN echo "install.server.dir=/opt/ibm-ucd/server" >> install.properties
RUN echo "install.server.web.always.secure=Y" >> install.properties
RUN echo "install.server.web.host=myserver.example.com" >> install.properties
RUN echo "install.server.web.https.port=8443" >> install.properties
RUN echo "install.server.web.ip=0.0.0.0" >> install.properties
RUN echo "install.server.web.port=8080" >> install.properties
RUN echo "database.type=mysql" >> install.properties
RUN echo "server.initial.password=root" >> install.properties
RUN echo "hibernate.connection.url=jdbc:mysql://localhost:3306/Urban" >> install.properties
RUN echo "hibernate.connection.username=admin" >> install.properties
RUN echo "hibernate.connection.password=vagrant" >> install.properties
RUN echo "database.mysql.port=3306" >> install.properties
RUN echo "rcl.server.url=27000@RCLServer.example.com" >> install.properties
RUN echo "server.initial.password=vagrant" >> install.properties




RUN cp /usr/share/java/mysql.jar /opt/ibm-ucd-install/lib/ext
RUN service mysql start &&\
chmod +x ./install-server.sh; sync; ./install-server.sh << EOF\
\n\
\n\
EOF

#RUN service mysql start &&\
#./install-server.sh <<EOF\
#\n\
#\n\
#EOF


#ENTRYPOINT service mysql start && /opt/ibm-ucd/bin/server run

EXPOSE 8443
EXPOSE 8080
