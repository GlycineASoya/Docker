FROM centos:centos7

ENV APPDYNAMICS_CONTROLLER_HOST_NAME $HOST
ENV APPDYNAMICS_CONTROLLER_PORT $PORT
ENV APPDYNAMICS_AGENT_ACCOUNT_ACCESS_KEY $KEY
ENV XMS 1024
ENV XMX 1536
ENV JAVA_HOME "/usr/lib/jvm/jre"

RUN yum -y update && \
    yum install -y java-1.8.0-openjdk && \
    yum install -y unzip && \
    mkdir -p /usr/local/DBAgent

COPY ./db-agent-4.5.8.1174.zip /usr/local/DBAgent
COPY ./start-dbagent.sh /usr/local/DBAgent
RUN cd /usr/local/DBAgent && unzip /usr/local/DBAgent/db-agent-4.5.8.1174.zip

WORKDIR /usr/local/DBAgent
RUN chmod +x /usr/local/DBAgent/start-dbagent.sh
ENTRYPOINT /usr/local/DBAgent/start-dbagent.sh

#docker run -d \
#-e APPDYNAMICS_CONTROLLER_HOST_NAME=192.168.100.31 \
#-e APPDYNAMICS_CONTROLLER_PORT=8090 \
#-e APPDYNAMICS_AGENT_ACCOUNT_ACCESS_KEY=ece40a6d-a497-4ff1-b91a-2f83fe4d3596 \
#--network dbagent --name db4.5.8.1174 ivlevinsky/dbagent-centos:4.5.8.1174