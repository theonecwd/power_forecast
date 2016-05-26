# Compile Android source code
## 编译安卓源代码
```
yum install glibc.i686  bison flex  gpref
source build/envsetup.sh
lunch 
make -j4

编译成功后配置环境变量 
为了使用模拟器
export PATH=$PATH:android-4.4.4_r1/out/host/linux-x86/bin

为编译goldfish
export PATH=$PATH:android-4.4.4_r1/prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin

```

## 运行模拟器
```
cd android/
source build/envsetup.sh
lunch
#没有上面两条指令可能无法启动模拟器
emulator -partition-size 1024 
或者
emulator -partition-size 1024 -kernel ../goldfish/arch/arm/boot/zImage
```
> android 模拟器启动需要四个文件，分别是zImage ,system.img , userdata.img ramdisk.img
    source build/envsetup.sh  && lunch 1 可以找到后面三个文件，故上述命令只制定了内核zImage,或者可以使用如下命令


//emulator -kernel  ./prebuilts/qemu-kernel/arm/kernel-qemu-armv7  -sysdir ./out/target/product/generic/ -system system.img -data userdata.img  -partition-size 1024

> http://blog.csdn.net/flydream0/article/details/7070392
