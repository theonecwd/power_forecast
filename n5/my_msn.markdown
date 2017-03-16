# msm
android对应虚拟上面的内核是goldfish，适用于N5等一些列手机的内核是msm,msm中有很多分支.
N5的code name 是hammerhead，在msm分支中适用于N5 android4.4 的分支是android-msm-hammerhead-3.4-kitkat-mr1，kitkat是android4.4的 code name
## download msm
git clone https://android.googlesource.com/kernel/msm.git msm
cd msm
git checkout android-msm-hammerhead-3.4-kitkat-mr1

## compile msm

```
cd android4.4.4
source build/envsetup.sh
lunch
```
> 上面source lunch貌似不是必须的
修改内核Makefile文件
```
#ARCH           ?= $(SUBARCH)
#CROSS_COMPILE  ?= $(CONFIG_CROSS_COMPILE:"%"=%)
ARCH            ?= arm
CROSS_COMPILE   ?= arm-eabi-
```
```
make menuconfig 或者make hammerhead_defconfig
make -j4
```

成功之后会生成zImage-dtb

## 生成boot.img
```
mkbooting --kernel zImage-dtb --ramdisk  android4.4.4/out/target/product/hammerhead/ramdisk.img --cmdline "console=ttyHSL0,115200,n8 androidboot.hardware=hammerhead user_debug=31 maxcpus=2 msm_watchdog_v2.enable=1" --base 0x00000000 --pagesize 2048 --ramdisk_offset 0x02900000 --tags_offset 0x02700000 --output my_boot.img
```

**关于上述参数请参考[这里](http://blog.csdn.net/wh_19910525/article/details/8200372)**

## 刷机

```
adb shell 
reboot bootloader

主机需要root权限,否则会显示wait for device
fastboot boot my_boot.img 

如果上面运行无误后,则可以执行fastboot flash boot my_boot.img
fastboot reboot

**fastboot boot my_boot.img 只是测试my_boot.img是否可用，不会写入,如果用fastboot flash boot boot my_boot.img则会写入**
```


## 加载jprobe_example.ko 模块
```
adb push jprobe_example.ko /sdcard/
adb shell
su
insmod jprobe_example.ko
lsmod 
cat /proc/kmsg
```
## reference:
- [1](http://abcdxyzk.github.io/blog/2014/12/22/android-kernel-2/)
- [2](http://www.2cto.com/kf/201404/296964.html)  文章mkbooting --kernel有误


