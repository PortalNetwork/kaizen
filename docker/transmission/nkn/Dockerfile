FROM golang:1.10-stretch

# apt-get
RUN apt-get update && apt-get upgrade -y

# for Dev only
RUN apt-get install lrzsz jq lsof psmisc git -y

# Set environment variables
ENV GOROOT=/usr/local/go
ENV PATH=$GOROOT/bin:$PATH
ENV GOPATH=/go
RUN echo -e "\n### Golang env" >> /etc/profile
RUN echo "export GOROOT=/usr/local/go" >> /etc/profile
RUN echo "export PATH=$GOROOT/bin:$PATH" >> /etc/profile
RUN echo "export GOPATH=/go" >> /etc/profile

RUN git clone https://github.com/nknorg/nkn.git /go/src/github.com/nknorg/nkn

WORKDIR /go/src/github.com/nknorg/nkn
RUN make glide
RUN make vendor
RUN make
RUN cp nknd nknc /usr/local/go/bin/

WORKDIR /nkn