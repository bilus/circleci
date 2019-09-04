FROM ubuntu:18.04

RUN apt-get update && apt-get install -y wget curl gnupg
RUN mkdir -p ~/.oya/bin && \
    cd ~/.oya/ && wget https://github.com/mozilla/sops/releases/download/3.3.1/sops_3.3.1_amd64.deb
RUN dpkg -i ~/.oya/sops_3.3.1_amd64.deb
RUN curl https://oya.sh/get | bash
RUN mv /usr/local/bin/oya ~/.oya/bin
ENV PATH="~/.oya/bin:${PATH}"
