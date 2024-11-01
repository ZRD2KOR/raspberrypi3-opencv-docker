FROM balenalib/raspberrypi3-debian:stretch

# Update Debian sources
RUN printf "deb http://archive.debian.org/debian/ jessie main\ndeb-src http://archive.debian.org/debian/ jessie main\ndeb http://security.debian.org jessie/updates main\ndeb-src http://security.debian.org jessie/updates main" > /etc/apt/sources.list

# Install dependencies for building and running OpenCV
RUN apt-get update && apt-get install -y --no-install-recommends \
    unzip \
    build-essential cmake pkg-config \
    checkinstall yasm \
    libjpeg-dev libtiff-dev libjasper-dev libpng12-dev libtiff5-dev \
    libavcodec-dev libavformat-dev libswscale-dev \
    libxine2-dev libv4l-dev \
    libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev \
    libgtk2.0-dev \
    libatlas-base-dev gfortran \
    libtbb2 libtbb-dev qt5-default \
    libmp3lame-dev libtheora-dev \
    libvorbis-dev libxvidcore-dev libx264-dev \
    libopencore-amrnb-dev libopencore-amrwb-dev \
    libavresample-dev \
    x264 v4l-utils \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get -y autoremove

# Install Python and packages
RUN apt-get install -y python2.7 python-pip && pip install --no-cache-dir numpy ipython

# Copy and install OpenCV
COPY download_build_install_opencv.sh download_build_install_opencv.sh
RUN chmod +x download_build_install_opencv.sh && ./download_build_install_opencv.sh
