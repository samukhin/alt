FROM busybox AS builder
WORKDIR /rootfs
RUN wget https://download.openvz.org/template/precreated/contrib/altlinux-p6-20120321-x86_64.tar.gz && \
tar -xf altlinux-p6-20120321-x86_64.tar.gz && \
rm -rf altlinux-p6-20120321-x86_64.tar.gz
RUN echo "rpm [cert6] http://mirror.yandex.ru/altlinux/p6/branch x86_64 classic" > /rootfs/etc/apt/sources.list.d/yandex.list && \
echo "rpm [cert6] http://mirror.yandex.ru/altlinux/p6/branch noarch classic" >> /rootfs/etc/apt/sources.list.d/yandex.list

FROM scratch
COPY --from=builder /rootfs /
RUN apt-get update && apt-get upgrade -y && apt-get clean
CMD /bin/bash
