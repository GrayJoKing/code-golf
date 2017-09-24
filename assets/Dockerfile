FROM alpine:edge

RUN apk add --no-cache bash curl gcc make musl-dev nodejs-npm openjdk8-jre perl

# Brotli
RUN curl -L https://github.com/google/brotli/archive/v1.0.1.tar.gz \
  | tar xzf -                                                      \
 && cd brotli-1.0.1                                                \
 && make -j`nproc`                                                 \
 && mv bin/brotli /usr/bin

# Closure Compiler
RUN curl http://dl.google.com/closure-compiler/compiler-20170910.tar.gz \
  | tar -zxf - -C /

# CSSO
RUN npm install -g csso-cli@1.0.0 csso@3.1.1

# Bashisms FTW.
RUN ln -snf /bin/bash /bin/sh

WORKDIR /work

CMD ["assets/build"]