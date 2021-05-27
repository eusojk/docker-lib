FROM ubuntu:18.04

RUN apt-get update \
    && apt-get install -y --no-install-recommends git make ca-certificates python3.8 python3-pip wget gfortran cmake

RUN mkdir -p /dssat47 \
    && mkdir -p /repo \
    && cd /repo \
    && git clone -b develop https://github.com/DSSAT/dssat-csm-os \
    && git clone -b develop https://github.com/DSSAT/dssat-csm-data \
    && cd dssat-csm-os \
    && cp -r /repo/dssat-csm-data/* Data/  \
    && mkdir build \
    && cd build  \
    && cmake -DCMAKE_INSTALL_PREFIX=/dssat47 -DCMAKE_BUILD_TYPE=RELEASE ..  \
    && make  \
    && make install

ENTRYPOINT ["/dssat47/dscsm047"]