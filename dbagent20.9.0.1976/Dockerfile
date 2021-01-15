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

COPY ./db-agent-20.9.0.1976.zip /usr/local/DBAgent
COPY ./start-dbagent.sh /usr/local/DBAgent
RUN cd /usr/local/DBAgent && unzip /usr/local/DBAgent/db-agent-20.9.0.1976.zip
COPY ./cacerts.jks /

WORKDIR /usr/local/DBAgent
RUN chmod +x /usr/local/DBAgent/start-dbagent.sh
ENTRYPOINT /usr/local/DBAgent/start-dbagent.sh