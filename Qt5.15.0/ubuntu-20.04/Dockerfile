FROM ubuntu:20.04

LABEL maintainer="paul.lemire350@gmail.com"

WORKDIR /usr/src/colorit

RUN apt update \
    &&\
    apt install -y \
        git \
        build-essential \
        perl \
        python \
        wget \
        '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev

RUN wget http://download.qt.io/official_releases/qt/5.15/5.15.0/single/qt-everywhere-src-5.15.0.tar.xz \
    &&\
    tar -xf qt-everywhere-src-5.15.0.tar.xz\
    &&\
    mkdir qt_build\
    &&\
    cd qt_build\
    &&\
    ../qt-everywhere-src-5.15.0/configure -opensource -nomake tests -nomake examples -confirm-license -no-pch -no-warnings-are-errors -release\
    &&\
    make module-qtbase && cd qtbase && make install && cd .. &&\
    make module-qtdeclarative && cd qtdeclarative && make install && cd .. &&\
    make module-qtquickcontrols && cd qtquickcontrols && make install && cd .. &&\
    make module-qtquickcontrols2 && cd qtquickcontrols2 && make install && cd .. &&\
    make module-qtgraphicaleffects && cd qtgraphicaleffects && make install && cd .. &&\
    make module-qtimageformats && cd qtimageformats && make install && cd .. &&\
    cd ../ && rm -rf qt_build qt-everywhere-src-5.15.0*
