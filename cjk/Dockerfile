FROM ubuntu:14.04.3
MAINTAINER Jack Chen <jack.chen.8@qq.com>
LABEL version='0.1' description="environment"

RUN apt-get update
RUN apt-get install -y git
RUN apt-get install -y vim

RUN git clone https://github.com/kkltcjk/install /root/install

WORKDIR /root/install
RUN /root/install/install.sh

EXPOSE 5000
