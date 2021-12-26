# AsusWRT Xiaomi
This is version of AsusWRT that works with Xiaomi Mi routers, based on MT7621 CPU.

## Supported devices
- Xiaomi MI R3G v1 - use R3G firmware
- Xiaomi MI R3G v2 and R4A - use R4A firmware
- Xiaomi AC2100, Xiaomi Redmi AC2100 - use R2100 firmware for black (cylinder) variant and use RM2100 firmware for white (6 antennas) variant
- Xiaomi R3P - use R3P firmware
- Mi WiFi 4 - not supported now (testers needed)

## How to install
1. Download image from Releases page or build it from source
2. Flash it to a router from stock firmware or bootloader

## Installation from stock firmware
Installation process is similar to OpenWRT
- NAND flash - image needs to be split into two parts: first 4MB and the rest - first part needs to be written to kernel1 partition, the rest to rootfs0. nvram variable flag_try_sys1_failed needs to be to 1, kernel0 partition should be erased
- NOR flash - image needs to be written to OS1 partition

## Installation from bootloader
- SPI flash - image needs to be written at 0x180000 offset
- NAND flash - image needs to be written at 0x600000 offset

## How to build image from source
1.先安装Ubuntu18.6

2.安装依赖
sudo rm -rf /etc/apt/sources.list.d/git-core-ubuntu-ppa-xenial.list
        sudo add-apt-repository ppa:git-core/ppa
        sudo dpkg --add-architecture i386
        sudo apt-get update
        sudo apt-get upgrade
        sudo apt-get install libncurses5 libncurses5-dev m4 bison gawk flex libstdc++-4.8-dev g++-multilib g++ \
        gengetopt git gitk zlib1g-dev autoconf autopoint libtool shtool autogen mtd-utils intltool sharutils \
        docbook-xsl-* libstdc++5 texinfo dos2unix xsltproc binutils u-boot-tools device-tree-compiler python \
        qemu gperf liblzo2-dev uuid-dev build-essential lzma-dev liblzma-dev lzma patch cmake intltool yodl yodl-doc \
        libglib2.0-dev gtk-doc-tools libc6-i386 lib32stdc++6 lib32z1 libelf1:i386 lib32ncurses5 libc6-dev-i386 libstdc++6:i386
 
 3.sudo chmod +x ./build.sh
 
 4.bash ./build.sh rt-mir4a model (currently available models are: rt-mir3g, rt-mir4a, rt-rm2100, rt-r2100)

## Missing features
- No dual-wan support

## Important note
- I do not take responsibility for any damages - you do everything on your own risk
