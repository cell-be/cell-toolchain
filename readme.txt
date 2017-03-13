
 ====================
  What does this do?
 ====================

  This program will automatically build and install a compiler and other
  tools used in the creation of homebrew software for the Cell BE.

 ==================
  How do I use it?
 ==================

 1) Set up your environment by installing the following software:

  autoconf, automake, bison, flex, gcc, libelf, make, makeinfo,
  ncurses, patch, python, subversion, wget, zlib, libtool, python,
  bzip2, gmp, pkg-config

  Specifically on debian-based systems, the following command line should
  be enough to install everything necessary:

  apt-get install autoconf automake bison flex gcc libelf-dev make \
    texinfo libncurses5-dev patch python subversion wget zlib1g-dev \
    libtool python-dev bzip2 libgmp3-dev pkg-config

 2) Add the following to your login script:

  export CELLDEV=/usr/local/celldev
  export PSL1GHT=$CELLDEV

  export PATH=$PATH:$CELLDEV/bin
  export PATH=$PATH:$CELLDEV/ppu/bin
  export PATH=$PATH:$CELLDEV/spu/bin

 3) Run the toolchain script:

  ./toolchain.sh

 =========================
  Run building in docker!
 =========================

 1) Get docker image:

  docker pull centos:6.8

 2) Create container:

  docker run -d -h c6tool --name c6tool \
             -v `pwd`/:/mount \
             -v `pwd`/celldev:/usr/local/ps3dev \
             centos:6.8 /bin/sh \
             -c 'while true; do echo hello world; sleep 1; done'

 3) Enter into container:

  docker exec -it c6tool bash

 4) Install following software and run build toolchain:

  a) for debian systems: (debian, ubuntu)

    apt-get install autoconf automake bison flex gcc gcc-c++ libelf-dev make \
      texinfo libncurses5-dev patch python subversion wget zlib1g-dev \
      libtool python-dev bzip2 libgmp3-dev pkg-config openssl-dev

  b) for redhat systems: (redhat, fedora, centos)

    yum install autoconf automake bison flex gcc gcc-c++ elfutils-libelf-devel make \
      texinfo ncurses-devel patch python subversion wget zlib-devel \
      libtool python-devel bzip2 gmp-devel pkgconfig openssl-devel

  cd /mount
  ./toolchain-sudo.sh
