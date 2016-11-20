FROM ubuntu:16.04
MAINTAINER Alberto Leal <albertonb@gmail.com>

RUN apt-get update && apt-get install -y \
 --no-install-recommends \
 build-essential \
 bzr \
 ca-certificates \
 curl \
 git \
 mercurial

# Install Go
RUN curl -s https://storage.googleapis.com/golang/go1.7.3.linux-amd64.tar.gz | tar -xzv -C /usr/local
ENV GOPATH /go
ENV GOROOT /usr/local/go
ENV PATH /usr/local/go/bin:/go/bin:/usr/local/bin:$PATH

# Install dependencies
RUN go get github.com/onsi/ginkgo/ginkgo
RUN go install github.com/onsi/ginkgo/ginkgo
RUN go get github.com/Masterminds/glide
