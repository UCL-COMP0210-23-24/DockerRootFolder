FROM mcr.microsoft.com/devcontainers/cpp:0-ubuntu-22.04

RUN apt-get update \
        && export DEBIAN_FRONTEND=noninteractive \
        && apt-get -y install --no-install-recommends clang-format openmpi-bin libopenmpi-dev gnuplot \
        && apt-get autoremove -y \
        && apt-get clean -y \
        && rm -rf /var/lib/apt/lists/*

# Download and Install FFTW
RUN     mkdir /usr/local/src/fftw \
        && cd /usr/local/src/fftw \
        && wget http://fftw.org/fftw-3.3.10.tar.gz \
        && tar -xvzf fftw-3.3.10.tar.gz \
        && cd fftw-3.3.10 \
        && mkdir build \
        && cd build \
        && cmake .. \
        && make -j \
        && make install

# Download and Install Catch2
RUN     mkdir /usr/local/src/Catch2 \
        && cd /usr/local/src/Catch2 \
        && git clone https://github.com/catchorg/Catch2.git \
        && cd Catch2 \
        && cmake -B build -DBUILD_TESTING=OFF \
        && cmake --build build \
        && cmake --install build/

# Download and Install Matplot++
RUN     mkdir /usr/local/src/matplot \
        && cd /usr/local/src/matplot \
        && git clone https://github.com/alandefreitas/matplotplusplus.git \
        && cd matplotplusplus \
        && cmake -B build/system -DMATPLOTPP_BUILD_EXAMPLES=OFF -DMATPLOTPP_BUILD_SHARED_LIBS=ON -DMATPLOTPP_BUILD_TESTS=OFF -DCMAKE_BUILD_TYPE=Release -DCMAKE_INTERPROCEDURAL_OPTIMIZATION=ON \
        && cmake --build build/system \
        && cmake --install build/system

ENV LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH