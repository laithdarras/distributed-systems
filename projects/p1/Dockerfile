# This is the modified version of Adam Weingram's (aweingram@ucmerced.edu) Dockerfile

FROM grpc/cxx:1.10

RUN apt-get update

RUN apt-get install -y wget build-essential libssl-dev

USER root

ENV HOME="/root"

ENV MY_INSTALL_DIR="${HOME}/.local"

RUN mkdir -p $MY_INSTALL_DIR

ENV PATH="${MY_INSTALL_DIR}/bin:$PATH"

RUN apt-get install -y git build-essential autoconf libtool pkg-config

RUN wget -q -O cmake-linux.sh https://github.com/Kitware/CMake/releases/download/v3.19.6/cmake-3.19.6-Linux-x86_64.sh

RUN sh cmake-linux.sh -- --skip-license --prefix=$MY_INSTALL_DIR

RUN rm cmake-linux.sh

RUN git clone --recurse-submodules -b v1.40.0 https://github.com/grpc/grpc.git /grpc

WORKDIR /grpc

RUN git submodule update --init

RUN mkdir -p cmake/build

#RUN pushd cmake/build
WORKDIR ./cmake/build

RUN cmake -DgRPC_INSTALL=ON -DgRPC_BUILD_TEST=OFF -DCMAKE_INSTALL_PREFIX=$MY_INSTALL_DIR ../..

RUN make -j 2

RUN make install

#RUN popd
WORKDIR /grpc

RUN mkdir -p ./third_party/abseil-cpp/cmake/build

#RUN pushd third_part/abseil-cpp/cmake/build
WORKDIR third_party/abseil-cpp/cmake/build

RUN cmake -DCMAKE_INSTALL_PREFIX=$MY_INSTALL_DIR -DCMAKE_POSITION_INDEPENDENT_CODE=TRUE ../..

RUN make -j 2

RUN make install

#RUN popd
WORKDIR /grpc

# Return to normal access

WORKDIR /

# ENTRYPOINT ["/bin/bash"]