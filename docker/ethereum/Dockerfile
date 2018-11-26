FROM ubuntu:xenial

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get -y -qq upgrade && \
    apt-get -y -qq install software-properties-common && \
    add-apt-repository ppa:ethereum/ethereum && \
    apt-get update && \
    apt-get -y -qq install geth solc && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ADD ./testnet.sh /root/testnet.sh
RUN chmod +x /root/testnet.sh

EXPOSE 8545
EXPOSE 30303

CMD /root/testnet.sh
