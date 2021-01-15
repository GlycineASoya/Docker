FROM ubuntu:16.04

COPY ./noip2 /etc/init.d
COPY ./makeinstall.sh /usr/local/src/noip-2.1.9-1/

RUN apt-get update -y && apt-get install -y make && \
        apt-get install -y wget && \
        apt-get install -y gcc && \
        apt-get install -y vim && \
        apt-get install -y expect

RUN chmod +x /etc/init.d/noip2 && chmod +x /usr/local/src/noip-2.1.9-1/makeinstall.sh
#RUN wget -O - http://www.eve-ng.net/repo/install-eve.sh | bash -i 
RUN        cd /usr/local/src/ && \
wget http://www.noip.com/client/linux/noip-duc-linux.tar.gz && \
tar xf noip-duc-linux.tar.gz && \
cd noip-2.1.9-1 && make && ./makeinstall.sh && service noip2 start

RUN sed -i -e 's/GRUB_CMDLINE_LINUX_DEFAULT=.*/GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0 noquiet"/' /etc/default/grub && \
        update-grub


EXPOSE 0-65535