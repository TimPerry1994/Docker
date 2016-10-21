FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt
RUN wget http://download.sonatype.com/nexus/3/nexus-3.0.2-02-unix.tar.gz
RUN tar -zxvf nexus-3.0.2-02-unix.tar.gz
RUN sudo ln -s nexus-3.0.2-02 nexus
RUN sed -i -e 's/run_as_user=""/run_as_user="root"/g' ./nexus/bin/nexus.rc
RUN sudo ln -s /opt/nexus/bin/nexus /etc/init.d/nexus

WORKDIR /etc/init.d
RUN chmod 755 nexus
RUN chown root nexus
RUN update-rc.d nexus defaults
ENTRYPOINT service nexus start && bash

EXPOSE 8081
