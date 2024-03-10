FROM ubuntu:jammy-20240227
MAINTAINER Lan Do <tuonglan7777777@gmail.com>

# Install bases
RUN apt-get update
RUN apt-get install -y wget python3 python3-dev python3-pip 

# Install openssl1
RUN wget -O - https://www.openssl.org/source/openssl-1.1.1u.tar.gz | tar zxf - 
WORKDIR /openssl-1.1.1u
RUN ./config --prefix=/usr/local
RUN make -j $(nproc) && make install_sw install_ssldirs
ENV SSL_CERT_DIR=/etc/ssl/certs 

# Install the sdk
RUN apt-get install -y build-essential libssl-dev ca-certificates libasound2 
RUN pip3 install azure-cognitiveservices-speech

# Install libgstreamer
RUN apt-get install -y libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools
