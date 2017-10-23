# Arch Linux ARM (Raspberry Pi 2)
FROM scratch
MAINTAINER TokinRing <support@gnetsolutions.net>
LABEL Description="Arch Linux ARM (Raspberry Pi 2)" Repository="armv7/armhf-archlinux"

ADD http://os.archlinuxarm.org/os/ArchLinuxARM-rpi-2-latest.tar.gz /

RUN pacman -Sy --noconfirm bash && pacman -Scc --noconfirm

CMD ["/bin/sh"]
