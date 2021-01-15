FROM centos:7
LABEL mainteiner='ilevinsk'

COPY . /home/

RUN yum update -y && yum install lsof openssh openssh-clients which libaio numactl tzdata ncurses-libs-5.x java-1.8.0-openjdk -y && yum clean all
RUN chown root:root /home/platform-setup-x64-linux-20.11.0.23788.sh
RUN chmod +x /home/platform-setup-x64-linux-20.11.0.23788.sh

EXPOSE 8090
EXPOSE 9191
EXPOSE 3388
EXPOSE 3700
EXPOSE 8181
EXPOSE 8021
EXPOSE 4848
EXPOSE 8020

WORKDIR /home
CMD ["./platform-setup-x64-linux-20.11.0.23788.sh"]