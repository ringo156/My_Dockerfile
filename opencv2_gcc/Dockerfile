FROM ubuntu:16.04

ENV QT_X11_NO_MITSHM=1

RUN apt-get update && apt-get install -y \
	cmake \
	unzip \
	wget \
	x11-apps \
	libgtk2.0-dev \ 
	pkg-config \
	libavcodec-dev \
	libavformat-dev \
	libswscale-dev \
	libtbb-dev \
	libqt4-dev \
	v4l-utils \
	libv4l-dev 
# 	--no-install-recommends

RUN cd /root \
	&& wget https://github.com/opencv/opencv/archive/2.4.13.6.zip \
	&& unzip 2.4.13.6.zip \
	&& cd ./opencv-2.4.13.6 \
	&& mkdir build \
	&& cd ./build \
	&& cmake -D WITH_TBB=OFF -D WITH_V4L=ON -D WITH_QT=ON \
	-D WITH_OPENGL=ON -D WITH_VTK=ON .. \
	&& make -j4 \
	&& make install \
	&& echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv.conf \
	&& ldconfig \
	&& echo "PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig" >> /etc/bash.bashrc \
	&& echo "export PKG_CONFIG_PATH" >> /etc/bash.bashrc \
	&& cd /root \
	&& rm -rf 2.4.13.6.zip opencv-2.4.13.6
