FROM ubuntu:20.04
ARG VERSION=1

LABEL	name="Spoofing attacks" \
		version="${VERSION}"

ENV TZ=Europe/Bucharest
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

WORKDIR /root

ENV DEBIAN_FRONTEND="noninteractive"

RUN apt-get update && \
	apt-get install -y iputils-ping net-tools iproute2 wget \
	git ssh vim dsniff curl tcpdump nmap driftnet iptables \
	python3 python3-pip tmux dnsutils apache2 

RUN pip3 install scapy mitmproxy
