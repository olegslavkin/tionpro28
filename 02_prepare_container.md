# Установка необходимых утилит
Устанавливаем необходимые пакеты
```
apt update && apt upgrade && apt install -y xz-utils make gcc flex bison bc file libssl-dev libncurses-dev parted udev dosfstools gcc-arm-linux-gnueabi kmod parted
```
Устанавливаем переменные окружения
```
export ARCH=arm
export CROSS_COMPILE=arm-linux-gnueabi-
export UBOOTVER=2019.04
export LINUXVER=5.1.2
export BSBOXVER=1.30.1
export ROOTFS=/mnt/rootfs
```
