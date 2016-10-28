FROM provisioning_maven
MAINTAINER Tim Perry

WORKDIR /opt/
COPY ./Shared/UCD_AG_Z_OS_ENG_6.2.2_TRIAL.zip /opt
RUN apt-get install -y unzip 
RUN unzip UCD_AG_Z_OS_ENG_6.2.2_TRIAL.zip

WORKDIR zipinstall
RUN unzip ibm-ucd-agent.zip

WORKDIR ibm-ucd-agent-install
RUN sed -i '20s/.*/locked\/agent.jms.remote.host=52.211.193.78/' example.agent.install.properties
RUN cp example.agent.install.properties install.properties

RUN sed -i '30isync' install-agent-from-file.sh && \
 chmod +x install-agent-from-file.sh; sync && ./install-agent-from-file.sh install.properties

#ENTRYPOINT /opt/urbancode/ibm-ucdagent/bin/agent run && bash

