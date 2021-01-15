#FROM debian:latest
FROM tomcat:9.0.38-jdk11-corretto

#APPDYNAMICS ARGS
ARG AGENT_VERSION

ENV APPDYNAMICS_AGENT_VERSION=20.9.0.30985

RUN yum -y update && \
	yum install -y unzip && \
#	yum install -y mysql mysql-server mysql-libs mysql-server && \
	mkdir -p /usr/local/AppAgent
COPY ./AppServerAgent-1.8-20.9.0.30985.zip /usr/local/AppAgent
#COPY /Users/ilevinsk/Work/AppD/agent-java-dotnet/java_agent/agent/java/appagent/core/build/install_image/ver20.11.0.0 /usr/local/AppAgent
COPY ./user-app/target/SampleServlet.war /usr/local/tomcat/webapps/
RUN cd /usr/local/AppAgent && unzip /usr/local/AppAgent/AppServerAgent-1.8-20.9.0.30985.zip


COPY ./Tomcat/catalina_appdynamics.sh /usr/local/tomcat/bin

EXPOSE 8080 
RUN chmod +x /usr/local/tomcat/bin/catalina_appdynamics.sh
WORKDIR /usr/local/tomcat/bin/
ENTRYPOINT /usr/local/tomcat/bin/catalina_appdynamics.sh

