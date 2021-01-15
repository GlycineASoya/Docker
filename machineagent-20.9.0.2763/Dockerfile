FROM centos:centos7

ENV APPDYNAMICS_CONTROLLER_HOST_NAME $HOST
ENV APPDYNAMICS_CONTROLLER_PORT $PORT
ENV APPDYNAMICS_AGENT_ACCOUNT_ACCESS_KEY $KEY
ENV JAVA_HOME "/usr/lib/jvm/jre"

RUN yum -y update && \
    yum install -y java-1.8.0-openjdk && \
    yum install -y unzip && \
    mkdir -p /usr/local/machineAgent

COPY ./machineagent-bundle-64bit-linux-20.11.0.2968.zip /usr/local/machineAgent
RUN cd /usr/local/machineAgent && unzip /usr/local/machineAgent/machineagent-bundle-64bit-linux-20.11.0.2968.zip
COPY ./cacerts.jks /usr/local/machineAgent
COPY ./controller-info.xml /usr/local/machineAgent/conf/

WORKDIR /usr/local/machineAgent
#CMD [/bin/bash]
ENTRYPOINT /usr/local/machineAgent/bin/machine-agent