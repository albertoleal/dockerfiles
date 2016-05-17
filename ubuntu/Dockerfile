FROM ubuntu:15.10
MAINTAINER Alberto Leal <albertonb@gmail.com>

RUN apt-get update && apt-get install -y \
 --no-install-recommends \
 build-essential \
 bzr \
 ca-certificates \
 curl \
 git \
 mercurial \
 vim

# Install/Configure golang
RUN curl -s https://storage.googleapis.com/golang/go1.6.2.linux-amd64.tar.gz | tar -xzv -C /usr/local 
ENV GOPATH /go
ENV GOROOT /usr/local/go
ENV PATH /usr/local/go/bin:/go/bin:/usr/local/bin:$PATH
