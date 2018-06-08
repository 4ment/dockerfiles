FROM debian:stretch

RUN  apt-get update -qq && apt-get install -y --no-install-recommends \
	build-essential \
	ca-certificates \
	cmake \
	git \
	libboost-all-dev \
	libgtest-dev \
	libnlopt-dev \
	pkg-config \
	wget
	
RUN wget https://github.com/BioPP/bpp-core/archive/v2.3.0.tar.gz && tar xvzf v2.3.0.tar.gz
RUN cd bpp-core-2.3.0 && mkdir _build && cd _build && cmake -DCMAKE_INSTALL_PREFIX=/usr/ .. && make && make install
RUN cd ../.. && rm v2.3.0.tar.gz
    
RUN wget https://github.com/BioPP/bpp-seq/archive/v2.3.0.tar.gz && tar xvzf v2.3.0.tar.gz
RUN cd bpp-seq-2.3.0 && mkdir _build && cd _build && cmake -DCMAKE_INSTALL_PREFIX=/usr/ .. && make && make install
RUN cd ../.. && rm v2.3.0.tar.gz
  
RUN wget https://github.com/BioPP/bpp-phyl/archive/v2.3.0.tar.gz && tar xvzf v2.3.0.tar.gz
RUN cd bpp-phyl-2.3.0 && mkdir _build && cd _build && cmake -DCMAKE_INSTALL_PREFIX=/usr/ .. && make && make install && cd ../..

RUN wget http://mirror.rise.ph/gnu/gsl/gsl-2.4.tar.gz && tar xvzf gsl-2.4.tar.gz
RUN cd gsl-2.4 && ./configure --prefix=/usr && make && make install && cd ../..

WORKDIR /usr/src/gtest
RUN cmake . && make && make install

WORKDIR /data
