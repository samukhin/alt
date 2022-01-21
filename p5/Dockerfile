FROM ubuntu:16.04 AS builder
RUN apt-get update && apt-get -y upgrade && apt-get -y install wget
WORKDIR /rootfs
RUN wget https://download.openvz.org/template/precreated/contrib/altlinux-5.1-x86_64.tar.gz && \
tar -xf altlinux-5.1-x86_64.tar.gz && \
rm -rf altlinux-5.1-x86_64.tar.gz
RUN echo "rpm [alt] http://mirror.yandex.ru/altlinux/5.0/branch x86_64 classic" > /rootfs/etc/apt/sources.list.d/yandex.list && \
echo "rpm [alt] http://mirror.yandex.ru/altlinux/5.0/branch noarch classic" >> /rootfs/etc/apt/sources.list.d/yandex.list && \
sed -i 's/62A18AD809AD1DDA342978242913F6A180EF7625/64032F109FD0C4331F572CC0DC9E95C2231114B3/' /rootfs/etc/apt/vendors.list.d/alt.list

FROM scratch
COPY --from=builder /rootfs /
RUN apt-get update && apt-get upgrade -y && apt-get clean
CMD /bin/bash
