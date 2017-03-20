# BeagleBone Green/Black Kernel Compilation Guide

*The build instructions were tested on Ubuntu 14.04.*

+ Install build tools
```bash
sudo apt-get install git lzop libssl-dev libncurses5-dev wget u-boot-tools git
```
+ Clone Git repository of forked Linux kernel
```bash
git clone https://github.com/henrix/beagle-linux.git && cd beagle-linux
```
+ Download hard float linearo compiler
```bash
wget https://releases.linaro.org/components/toolchain/binaries/5.4-2017.01/arm-linux-gnueabihf/gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
tar xf gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
```
+ Clean build directory and create temporary directory
```bash
make mrproper && mkdir modules_tmp
```
+ Generate kernel config
```bash
make ARCH=arm CROSS_COMPILE=gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf- bb.org_defconfig
```
+ Enable driver for CTAG face2|4 Audio Card (→ Device Drivers → Sound card support → Advanced Linux Sound Architecture → ALSA for SoC audio support → SoC Audio Support for CTAG face-2-4 Audio Card (AD1938))
```bash
make ARCH=arm CROSS_COMPILE=gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf- menuconfig
```
+ Compile the kernel
```bash
make ARCH=arm CROSS_COMPILE=gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf- -j9
```
+ Compile U-Boot image and device tree blobs
```bash
make ARCH=arm CROSS_COMPILE=gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf- uImage dtbs LOADADDR=0x80008000 -j9
```
+ Compile kernel modules
```bash
make ARCH=arm CROSS_COMPILE=gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf- modules -j9
```
+ Install compiled kernel and modules to temporary directory
```bash
make ARCH=arm CROSS_COMPILE=gcc-linaro-5.4.1-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf- INSTALL_MOD_PATH=modules_tmp modules_install
```
+ Copy kernel image to SD card
```bash
sudo cp arch/arm/boot/zImage /media/$USER/rootfs/boot/vmlinuz-4.1.18+
```
+ Copy kernel modules to SD card
```bash
sudo cp -r modules_tmp/lib/ /media/$USER/rootfs/
```
+ Copy device tree blobs to SD card
```bash
sudo mkdir -p /media/$USER/rootfs/boot/dtbs/4.1.18+ && cp -r arch/arm/boot/dts/*.dtb /media/$USER/rootfs/boot/dtbs/4.1.18+/
```
+ Copy kernel configuration to SD card
```bash
sudo cp .config /media/$USER/rootfs/boot/config-4.1.18+
```
## The next steps must be executed directly on the BeagleBone Black/Green
+ Insert the following line into **/boot/uEnv.txt** to use the new kernel
```bash
uname_r=4.1.18+
```
+ Insert the following line into **/boot/uEnv.txt** to use the custom device tree blob
```bash
dtb=am335x-bonegreen-ctag-face.dtb
```
+ Reboot to use new kernel
```bash
reboot
```
+ Generate initramfs image and reboot again
```bash
sudo update-initramfs -c -k $(uname -r)
reboot
```
+ Clone CTAG face2|4 AudioCard repo
```bash
git clone https://github.com/ctag-fh-kiel/ctag-face-2-4.git && cd ctag-face-2-4/device-tree-overlays
```
+ Compile Device Tree Overlays for CTAG face2|4 Audio Card
```bash
dtc -O dtb -o BB-CTAG-FACE-8CH-00A0.dtbo -b 0 -@ BB-CTAG-FACE-8CH-00A0.dts
sudo mv BB-CTAG-FACE-8CH-00A0.dtbo /lib/firmware
```
+ Load kernel modules for CTAG face2|4 Audio Card with Bone-Cape-Manager
```bash
sudo sh -c "echo 'BB-CTAG-FACE-8CH' > /sys/devices/platform/bone_capemgr/slots"
```
