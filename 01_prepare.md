# Подготовка хостовой ОС и загрузка исходных файлов
Требования к хостовой ОС:
- Ubuntu Linux (или любой другой с поддержкой docker)
- Установленный Docker

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
Codename:       bionic
$ docker -v
Docker version 18.09.6, build 481bc77
```
Устанавливаем переменные окружения, а также указываем базовую директорию где будет осуществляется сборка.
Если необходимо, можно заменить версии пакетов на другие.
```
export TIONPRO28=~/tionpro28
export UBOOTVER=2019.04
export LINUXVER=5.1.2
export BSBOXVER=1.30.1
```
Создаем необходимые каталоги, а затем скачиваем минимальные базовые пакеты (загрузчик U-Boot, ядро Linux и также Busybox)
```
mkdir -p ${TIONPRO28}/{src,build,boot,rootfs}
cd ${TIONPRO28}/src

wget -q ftp://ftp.denx.de/pub/u-boot/u-boot-${UBOOTVER}.tar.bz2
wget -q https://mirror.yandex.ru/pub/linux/kernel/v5.x/linux-${LINUXVER}.tar.xz
wget -q https://busybox.net/downloads/busybox-${BSBOXVER}.tar.bz2
```
Запускаем контейнер. Все последующие шаги (если не сказано иначе) делаются внутри изолированного контейнера docker.
```
cd ${TIONPRO28}
docker run -it --privileged -v $(pwd):/mnt -w /mnt -h tionpro28-build --net host ubuntu:18.10 bash
```
