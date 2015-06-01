FROM ubuntu:14.04
MAINTAINER cole brown

RUN apt-get update
RUN apt-get -y dist-upgrade
RUN apt-get install -y xz-utils libgmp10 libgmp-dev build-essential zlib1g-dev curl
WORKDIR /root
ADD https://www.haskell.org/ghc/dist/7.10.1/ghc-7.10.1-x86_64-unknown-linux-deb7.tar.xz /root/
RUN tar xJf ghc-7.10.1-x86_64-unknown-linux-deb7.tar.xz && rm ghc-7.10.1-x86_64-unknown-linux-deb7.tar.xz
WORKDIR /root/ghc-7.10.1
RUN ./configure && make install && cd /root && rm -rf ghc-7.10.1
WORKDIR /root
ADD https://www.haskell.org/cabal/release/cabal-install-1.22.4.0/cabal-install-1.22.4.0.tar.gz /root/
RUN tar xzf cabal-install-1.22.4.0.tar.gz
WORKDIR /root/cabal-install-1.22.4.0
RUN ./bootstrap.sh
ENV PATH /root/.cabal/bin:$PATH
WORKDIR /root
RUN rm -rf cabal-install-1.22.4.0*
RUN cabal update
RUN cabal install alex happy

