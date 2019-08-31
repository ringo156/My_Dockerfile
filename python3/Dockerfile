FROM ubuntu:16.04

ENV http_proxy 'http:/proxy/:port'
ENV https_proxy 'http://proxy:port'
ENV ftp_proxy 'http://proxy:port'
ENV socks_proxy 'http://proxy:port'
ENV no_proxy '127.0.0.1,localhost'

RUN apt-get update && apt-get upgrade -y
# Build Python3.6
RUN apt-get install -y \
	wget \
	build-essential \
	libbz2-dev \
	libdb-dev \
	libreadline-dev \
	libffi-dev \
	libgdbm-dev \
	liblzma-dev \
	libncursesw5-dev \
	libsqlite3-dev \
	libssl-dev \
	zlib1g-dev \
	uuid-dev \
	tk-dev

RUN cd /root/ && wget https://www.python.org/ftp/python/3.6.7/Python-3.6.7.tgz \
	 && tar xzf Python-3.6.7.tgz \
	 && cd Python-3.6.7 \
	 && ./configure --enable-optimizations \
	 && make -j4 \
	 && make altinstall
RUN ln -s /usr/local/bin/python3.6 /usr/bin/python \
	 && ln -s /usr/local/bin/python3.6 /usr/bin/python3 \
	 && ln -s /usr/local/bin/pip3.6 /usr/bin/pip3 \
	 && ln -s /usr/local/bin/pip3.6 /usr/bin/pip

RUN rm -rf /root/Python-3.6.7 /root/Python-3.6.7.tgz
