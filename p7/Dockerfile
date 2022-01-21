FROM busybox AS builder
WORKDIR /rootfs
RUN wget http://ftp.altlinux.org/pub/distributions/ALTLinux/images/p7/starterkits/altlinux-p7-ovz-generic-20160312-x86_64.tar.xz && \
tar -xf altlinux-p7-ovz-generic-20160312-x86_64.tar.xz && \
rm -rf altlinux-p7-ovz-generic-20160312-x86_64.tar.xz

FROM scratch
COPY --from=builder /rootfs /
RUN apt-get update && apt-get upgrade -y && apt-get clean
CMD /bin/bash
