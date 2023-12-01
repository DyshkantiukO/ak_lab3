# ak_lab3
test3

#part1
commands for export:
```
export ARCH=arm
```
```
export PATH=/opt/gcc-arm-8.3-2019.03-x86_64-arm-linux-gnueabihf/bin:$PATH
```
```
export CROSS_COMPILE="ccache arm-linux-gnueabihf-"
```
```
export KDIR=$HOME/repos/linux-stable
```
```
make
```
#part2
move hello.ko to ~/repos/busybox/_install and rebuild the image
```
cd ~/repos/busybox/_install
```
```
find . | cpio -o -H newc | gzip > ../rootfs.cpio.gz
```
```
cd ..
```
#part3
commands for start QEMU:
```
qemu-system-arm -kernel _install/boot/zImage -initrd rootfs.cpio.gz -machine virt -nographic -m 512 --append "root=/dev/ram0 rw console=ttyAMA0,115200 mem=512M"
```
#part4
commands for check:
```
insmod hello.ko
```
```
modinfo hello.ko
```
```
rmmod hello
```
