FROM ubuntu:19.04

RUN apt-get update
RUN apt-get install -y wget curl gnupg git \
  apt-transport-https ca-certificates software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
RUN apt-get update
RUN apt-get install -y docker-ce

RUN mkdir -p ~/.oya/bin && \
    cd ~/.oya/ && wget https://github.com/mozilla/sops/releases/download/3.3.1/sops_3.3.1_amd64.deb
RUN dpkg -i ~/.oya/sops_3.3.1_amd64.deb

ENV OYA_VERSION=v0.0.18.pre1
RUN curl https://oya.sh/get | bash -s $OYA_VERSION
