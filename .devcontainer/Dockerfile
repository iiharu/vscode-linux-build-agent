FROM mcr.microsoft.com/devcontainers/base:trixie

ARG CT_NG_VERSION=1.26.0

RUN --mount=type=cache,target=/var/cache/apt,sharing=locked \
    --mount=type=cache,target=/var/lib/apt,sharing=locked \
    apt-get update && export DEBIAN_FRONTEND=noninteractive \
 && apt-get -y install --no-install-recommends \
    autoconf \
    automake \
    bison \
    bzip2 \
    flex \
    g++ \
    gawk \
    gcc \
    git \
    gperf \
    help2man \
    libncurses5-dev \
    libtool \
    libtool-bin \
    make \
    meson \
    ninja-build \
    patch \
    python3-dev \
    rsync \
    texinfo \
    unzip \
    wget \
    xz-utils

RUN wget http://crosstool-ng.org/download/crosstool-ng/crosstool-ng-${CT_NG_VERSION}.tar.bz2 \
 && tar xf crosstool-ng-${CT_NG_VERSION}.tar.bz2 \
 && cd crosstool-ng-${CT_NG_VERSION} \
 && ./configure --prefix=/usr/local \
 && make -j"$(nproc)" \
 && make install \
 && cd .. \
 && rm -rf crosstool-ng-${CT_NG_VERSION} crosstool-ng-${CT_NG_VERSION}.tar.bz2
