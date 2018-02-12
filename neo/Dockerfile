From ubuntu:16.04

MAINTAINER kerwin kerwin@geek.ink

RUN apt-get update && apt-get install -y git curl unzip wget \
	apt-transport-https libleveldb-dev sqlite3 libsqlite3-dev libunwind8-dev && \
	curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && \
	mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
RUN	sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list' && \
	apt-get update && apt-get install -y dotnet-sdk-2.1.4

RUN	wget https://github.com/neo-project/neo-cli/releases/download/v2.7.1/neo-cli-ubuntu.16.04-x64.zip && \
	unzip neo-cli-ubuntu.16.04-x64.zip

RUN apt-get install -y supervisor
ADD supervisord.conf /etc/supervisord.conf

WORKDIR /neo-cli

EXPOSE 10332 10333 10334
CMD ["supervisord", "-n", "-c", "/etc/supervisord.conf"]
