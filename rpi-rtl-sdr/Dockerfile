FROM multiarch/alpine:armhf-latest-stable

RUN apk add --no-cache libusb git build-base cmake libusb-dev && \
    git clone git://git.osmocom.org/rtl-sdr.git /tmp/rtl-sdr && \
    mkdir /tmp/rtl-sdr/build && cd /tmp/rtl-sdr/build && \
    cmake ../ -DINSTALL_UDEV_RULES=ON -DDETACH_KERNEL_DRIVER=ON && make && make install ; \
    cd / && rm -r /tmp/rtl-sdr && \
    find /usr/local/bin -type f -exec strip -p --strip-debug {} \; && \
    apk del git build-base cmake libusb-dev

CMD ["/bin/sh"]