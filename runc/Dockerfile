FROM albertoleal/wily
MAINTAINER Alberto Leal <albertonb@gmail.com>

RUN apt-get update && apt-get install -y \
	--no-install-recommends \
	make \
	jq \
	apparmor \
	libapparmor-dev

RUN set -x \
	&& export SECCOMP_PATH="$(mktemp -d)" \
	&& curl -fsSL "https://github.com/seccomp/libseccomp/releases/download/v2.3.1/libseccomp-2.3.1.tar.gz" \
		| tar -xzC "$SECCOMP_PATH" --strip-components=1 \
	&& ( \
		cd "$SECCOMP_PATH" \
		&& ./configure --prefix=/usr/local \
		&& make \
		&& make install \
		&& ldconfig \
	) \
	&& rm -rf "$SECCOMP_PATH"

RUN set -x \
  && git clone git://github.com/opencontainers/runc.git "$GOPATH/src/github.com/opencontainers/runc" \
  && cd "$GOPATH/src/github.com/opencontainers/runc" \
  && make BUILDTAGS="seccomp apparmor selinux" \
  && make install

RUN set -x \
  && mkdir /containers

WORKDIR /containers
