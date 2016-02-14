# BeagleBone Green/Black Kernel Compilation Guide

*The build instructions were tested on Ubuntu 14.04.*

+ Install required build tools
```bash
sudo apt-get install gcc-arm-linux-gnueabi git lzop libssl-dev libncurses5-dev wget u-boot-tools
```
+ Clone Git repository of forked Linux kernel
```bash
git clone https://github.com/henrix/beagle-linux.git && cd beagle-linux
```
+ Clean build directory and create temporary directory
```bash
make mrproper && mkdir modules_tmp
```
+ Generate kernel config
```bash
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- bb.org_defconfig
```
+ *Download realtime patch (optional)*
```bash
wget https://www.kernel.org/pub/linux/kernel/projects/rt/4.1/patch-4.1.10-rt11.patch.xz
```
+ *Apply realtime patch (optional, not recommended)*
```bash
xzcat ../patch-4.1.10-rt11.patch.xz | patch -p1
```
+ *Make some custom configurations, e.g. enable realtime scheduler (optional, not recommended)*
```bash
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- menuconfig
```
+ Compile the kernel
```bash
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- -j9
```
+ Compile U-Boot image and device tree blobs
```bash
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- uImage dtbs LOADADDR=0x80008000 -j9
```
+ Compile kernel modules
```bash
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- modules -j9
```
+ Install compiled kernel and modules to temporary directory
```bash
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- INSTALL_MOD_PATH=modules_tmp modules_install
```
+ Copy kernel image to SD card
```bash
cp arch/arm/boot/zImage ~/rootfs/boot/vmlinuz-4.1.10+
```
+ Copy kernel modules to SD card
```bash
cp -r modules_tmp/lib/ ~/mnt/rootfs/
```
+ Copy device tree blobs to SD card
```bash
mkdir -p ~/mnt/rootfs/boot/dtbs/4.1.10+ && cp -r arch/arm/boot/dts/*.dtb ~/mnt/rootfs/boot/dtbs/4.1.10+/
```
+ Copy kernel configuration to SD card
```bash
cp .config ~/mnt/rootfs/boot/config-4.1.10+
```
+ Copy Bone Cape for CTAG face2|4 Audio Card to SD card
```bash
cp BBB-AD193X-* ~/mnt/rootfs/root
```
+ Insert the following line into **/boot/uEnv.txt** to use the new kernel
```bash
uname_r=4.1.10+
```
+ Insert the following line into **/boot/uEnv.txt** to use the custom device tree blob
```bash 
dtb=am335x-bonegreen-audiocard.dtb
```
+ Clone offical BeagleBone Cape Git repository, install device tree compiler, generate initramfs image and reboot
```bash
git clone https://github.com/beagleboard/bb.org-overlays && cd ./bb.org-overlays
./dtc-overlay.sh
./install.sh
```
+ Compile Bone Cape for CTAG face2|4 Audio Card
```bash
dtc -O dtb -o BBB-AD193X-8TDM-00A0.dtbo -b 0 -@ BBB-AD193X-8TDM-00A0.dts
mv BBB-AD193X-8TDM-00A0.dtbo /lib/firmware
```
+ Load Bone Cape for CTAG face2|4 Audio Card with Bone-Cape-Manager
```bash
sh -c "echo 'BBB-AD193X-8TDM' > /sys/devices/platform/bone_capemgr/slots"
```

<!---
This is [on GitHub](https://github.com/jbt/markdown-editor) so let me know if I've b0rked it somewhere.


Props to Mr. Doob and his [code editor](http://mrdoob.com/projects/code-editor/), from which
the inspiration to this, and some handy implementation hints, came.

### Stuff used to make this:

 * [markdown-it](https://github.com/markdown-it/markdown-it) for Markdown parsing
 * [CodeMirror](http://codemirror.net/) for the awesome syntax-highlighted editor
 * [highlight.js](http://softwaremaniacs.org/soft/highlight/en/) for syntax highlighting in output code blocks
 * [js-deflate](https://github.com/dankogai/js-deflate) for gzipping of data to make it fit in URLs
-->
