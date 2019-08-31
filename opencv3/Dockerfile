FROM ubuntu:16.04

ENV QT_X11_NO_MITSHM=1

RUN apt-get update && apt-get upgrade -y

# Build OpenCV3
RUN apt-get install -y \
	 cmake \
	 pkg-config \
	 wget \
	 build-essential \
	 unzip \
	 libtbb-dev \
	 qt5-default \
	 libgtk2.0-dev \
	 libavcodec-dev \
	 libavformat-dev \
	 libswscale-dev \
	 libv4l-dev \
	 libxvidcore-dev \
	 libx264-dev \
	 libgtk-3-dev \
	 libhdf5-dev \
	 libwebp-dev \
	 libjpeg-dev \
	 libpng-dev \
	 libtiff-dev \
	 libjasper-dev \
	 libatlas-base-dev \
	 gfortran
RUN pip3.6 install numpy

RUN cd /root/ \
	 && wget https://github.com/opencv/opencv/archive/3.4.7.zip \
	 && unzip 3.4.7.zip \
	 && cd ./opencv-3.4.7 \
	 && mkdir build \
	 && cd ./build \
	 && cmake -D CMAKE_BUILD_TYPE=RELEASE \
	 -D WITH_TBB=ON -D WITH_V4L=ON -D WITH_QT=ON \
	 -D WITH_OPENGL=ON -D WITH_VTK=ON \
	 -D INSTALL_PYTHON_EXAMPLES=OFF \
	 -D INSTALL_C_EXAMPLES=OFF \
# 	 -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.4.3/modules \
	 -D PYTHON_EXECUTABLE=/usr/local/bin/python3.6 ..\
	 && make -j4 \
	 && make install

RUN apt-get install -y x11-apps

RUN rm -rf /root/opencv-3.4.7 /root/3.4.7.zip

