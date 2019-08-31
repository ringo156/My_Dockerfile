FROM python:3.6.7

ENV QT_X11_NO_MITSHM=1

RUN apt-get update && apt-get upgrade -y

# Build OpenCV4
RUN apt-get install -y \
	 cmake \
	 build-essential \
	 pkg-config \
	 wget \
	 unzip \
# GUI
	 qt5-default \
	 libvtk6-dev \
	 zlib1g-dev \
	 libjpeg-dev \
	 libwebp-dev \
	 libpng-dev \
	 libtiff5-dev \
	 libjasper-dev \
	 libopenexr-dev \
	 libgdal-dev \
# Video I/O
	 libdc1394-22-dev \
	 libavcodec-dev \
	 libavformat-dev \
	 libswscale-dev \
	 libtheora-dev \
	 libvorbis-dev \
	 libxvidcore-dev \
	 libx264-dev \
	 yasm \
	 libopencore-amrnb-dev \
	 libopencore-amrwb-dev \
	 libv4l-dev \
	 libxine2-dev \
# Parallelism and linear algebra libraries:
	 libtbb-dev \
	 libeigen3-dev 
RUN pip3.6 install numpy

RUN cd /root/ \
	 && wget https://github.com/opencv/opencv/archive/4.1.0.zip \
	 && unzip 4.1.0.zip 

RUN cd /root/opencv-4.1.0 \
	 && mkdir build \
	 && cd ./build \
	 && cmake -D CMAKE_BUILD_TYPE=RELEASE \
	 -D WITH_TBB=ON -D WITH_V4L=ON -D WITH_QT=ON \
	 -D WITH_OPENGL=ON -D WITH_VTK=ON -D WITH_GDAL=ON \
	 -D INSTALL_PYTHON_EXAMPLES=OFF \
	 -D INSTALL_C_EXAMPLES=OFF \
# 	 -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.4.3/modules \
	 -D PYTHON_EXECUTABLE=/usr/local/bin/python3.6 ..\
	 && make -j4 \
	 && make install \
	 && ldconfig

RUN apt-get install -y x11-apps

RUN rm -rf /root/opencv-4.1.0 /root/4.1.0.zip

