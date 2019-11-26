FROM debian

ENV TS3SERVER_LICENSE=accept

WORKDIR /home/teamspeak

EXPOSE 9987/udp 10011 30033

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y wget bzip2
RUN	wget http://dl.4players.de/ts/releases/3.8.0/teamspeak3-server_linux_amd64-3.8.0.tar.bz2 && \
	tar -xvf teamspeak3-server_linux_amd64-3.8.0.tar.bz2
WORKDIR teamspeak3-server_linux_amd64
ENTRYPOINT ["./ts3server"]

# How to build it?
# docker build -t ex01 .

# How to run it?
# docker run --rm -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01


