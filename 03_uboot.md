# Сборка загрузчика U-Boot

```
tar xf /mnt/src/u-boot-${UBOOTVER}.tar.bz2 -C /mnt/build
cd /mnt/build/u-boot-${UBOOTVER}
make ARCH=arm mx28evk_defconfig O=../u-boot-${UBOOTVER}-build
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- u-boot.sb O=../u-boot-${UBOOTVER}-build
../u-boot-${UBOOTVER}-build/tools/mxsboot sd ../u-boot-${UBOOTVER}-build/u-boot.sb /mnt/boot/u-boot.sb
```
Для сборки образа ядра Linux uImage необходима будет утилита mkimage
```
ln -s /mnt/build/u-boot-${UBOOTVER}-build/tools/mkimage /usr/bin/mkimage
```
