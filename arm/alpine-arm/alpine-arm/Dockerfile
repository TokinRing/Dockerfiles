FROM scratch
MAINTAINER TokinRing [support@gnetsolutions.net]

ENV ARCH armhf
ENV RELEASE v3.6
ENV VERSION 3.6.0

ADD http://dl-cdn.alpinelinux.org/alpine/${RELEASE}/releases/${ARCH}/alpine-minirootfs-${VERSION}-${ARCH}.tar.gz /

RUN apk update && apk --no-cache add bash alpine-baselayout apk-tools alpine-keys libc-utils

CMD ["/bin/bash"]
