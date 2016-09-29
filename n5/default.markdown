# 为Nexus5编译Android固件

## 初始化编译环境
```
cd android4.4.4
. build/envsetup.sh

```

##  加载机型
lunch  选择 aosp_hammerhead-userdebug

|device    |    code name    |  build configuration|
|:------:|:-----------:| :--------------------:|
|Nexus 6     |shamu |aosp_shamu-userdebug|
|Nexus Player|    fugu|    aosp_fugu-userdebug|
|Nexus 9 |    volantis (flounder) |    aosp_flounder-userdebug|
|Nexus 5 (GSM/LTE)|   hammerhead | aosp_hammerhead-userdebug|
|Nexus 7 (Wi-Fi)  |   razor (flo) |    aosp_flo-userdebug
|Nexus 7 (Mobile) |  razorg (deb) |   aosp_deb-userdebug
|Nexus 10  |  mantaray (manta)  |  full_manta-userdebug
|Nexus 4   |  occam (mako)  |  full_mako-userdebug
|Nexus 7 (Wi-Fi) |    nakasi (grouper)  |  full_grouper-userdebug
|Nexus 7 (Mobile)|    nakasig (tilapia) |  full_tilapia-userdebug
|Galaxy Nexus (GSM/HSPA+) |  yakju (maguro) |  full_maguro-userdebug
|Galaxy Nexus (Verizon) |  mysid (toro)  |  aosp_toro-userdebug
|Galaxy Nexus (Experimental)|     mysidspr (toroplus)|     aosp_toroplus-userdebug
|PandaBoard (Archived) |  panda |  aosp_panda-userdebug
|Motorola Xoom (U.S. Wi-Fi)|  wingray |    full_wingray-userdebug
|Nexus S  |   soju (crespo) |  full_crespo-userdebug
|Nexus S 4G|  sojus (crespo4g)|    full_crespo4g-userdebug3.2


## 生成驱动目录
需要安装驱动，否则一直停留在google的黑色界面
|HARDWARE COMPONENT | COMPANY   |  DOWNLOAD |   MD5 CHECKSUM |   SHA-1 CHECKSUM |
|:-----------------:|:---------:|:---------:|:--------------:|:----------------:|
|NFC, Bluetooth, Wi-Fi |  Broadcom | [下载](https://dl.google.com/dl/android/aosp/broadcom-hammerhead-lrx22c-964d941e.tgz) |   2c398994e37093df51b105d63f0eb611 |    991346159c95ae75f760014a6822b8b3e8667700
|Camera, Sensors, Audio | LG | [下载](https://dl.google.com/dl/android/aosp/lge-hammerhead-lrx22c-95a9d465.tgz)|    74cf8235e6bb04da28b2ff738b13eee9|    175dd5bae81bb54030d072cb0f0b4ec81eb3f71f
|Graphics, GSM, Camera, GPS, Sensors, Media, DSP, USB|    Qualcomm |  [ 下载](https://dl.google.com/dl/android/aosp/lge-hammerhead-lrx22c-95a9d465.tgz)|   0a43395e175d3de3dc312d8abdcb4f20 |    007cf9d49f0409d5c703e7f2811fd153fee22353

**下载完成后,解压出来是三个.sh文件,放到Android源码目录下面,然后执行.会将相关驱动放到vender目录下面.**

[下载官网](https://developers.google.com/android/nexus/drivers#fugumra58n)

## 执行编译命令
make -j4

## 刷机命令
Nexus5关机状态下,长按音量下+电源,即可进入recovery模式, 然后在源码根目录下执行下面命令:
source  build/envsetup.sh 
lunch
fastboot -w flashall

或者
**root权限**
adb shell
reboot bootloader
source  build/envsetup.sh 
lunch
fastboot -w flashall

adb fastboot这些命令在编译android源代码后加入了环境变量

## problem 
如果遇到开机一听停留在Google的显示界面，那么则没有安装驱动，安装相应的驱动就可以成功开机，驱动的安装方法参考上文，或者文章结尾的参考链接

[参考](http://androidperformance.com/2015/02/04/build-rom-for-nexus5.html)
