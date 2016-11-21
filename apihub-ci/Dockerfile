FROM ubuntu:16.04
MAINTAINER Alberto Leal <albertonb@gmail.com>

RUN apt-get update && apt-get install -y \
 --no-install-recommends \
 build-essential \
 bzr \
 ca-certificates \
 curl \
 git \
 wget \
 unzip \
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
RUN wget https://releases.hashicorp.com/consul/0.7.1/consul_0.7.1_linux_amd64.zip && \
  unzip consul_0.7.1_linux_amd64.zip && \
  mv consul /usr/local/bin && \
  rm consul_0.7.1_linux_amd64.zip

ENV DOCKER_BUCKET get.docker.com
ENV DOCKER_VERSION 1.12.3
ENV DOCKER_SHA256 626601deb41d9706ac98da23f673af6c0d4631c4d194a677a9a1a07d7219fa0f

RUN set -x \
	&& curl -fSL "https://${DOCKER_BUCKET}/builds/Linux/x86_64/docker-${DOCKER_VERSION}.tgz" -o docker.tgz \
	&& echo "${DOCKER_SHA256} *docker.tgz" | sha256sum -c - \
	&& tar -xzvf docker.tgz \
	&& mv docker/* /usr/local/bin/ \
	&& rmdir docker \
	&& rm docker.tgz \
	&& docker -v
