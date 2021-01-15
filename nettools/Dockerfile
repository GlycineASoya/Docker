FROM debian:latest
LABEL maintainter="ilevinsk"

RUN apt update && \
	apt install -y traceroute && \
	apt install -y curl && \
	apt clean

ENTRYPOINT ["/bin/bash"]
