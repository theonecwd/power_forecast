# 动态加载
mkdir hello
touch hello/hello.c

## hello/hello.c 
```c
#include <linux/module.h>  
#include <linux/init.h>  

MODULE_LICENSE("GPL");  
static int __init hello_init(void)  {  
    printk(KERN_ERR "Hello world init\n");  
    return 0;  
}  

static void __exit hello_exit(void)  {  
    printk(KERN_ERR "Hello world exit\n");  
} 

module_init(hello_init);  
module_exit(hello_exit);  
```
## hello/Makefile
touch hello/Makefile
```
obj-m := hello.o

#内核在哪
KID := /home/cwd/fedora/cwd/paper/goldfish 
PWD := $(shell pwd)
ARCH =arm
CROSS_COMPILE=arm-eabi-
cc=$(CROSS_COMPILE)gcc
LD=$(CROSS_COMPILE)ld

all:
    make -C $(KID) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) M=$(PWD) modules

clean:
    rm -rf *.o .cmd *.ko *.mod.c .tmp_versions

```
> KID表示内核源码目录，这种方式适用于嵌入式开发的交叉编译，KID目录中包含了内核驱动模块所需要的各种头文件及依赖。若在PC机开发内核模块则应使用
```
    #KERN_DIR = /usr/src/$(shell uname -r)
    #KERN_DIR = /lib/modules/$(shell uname -r)/build 
```
    -C表示 指定进入指定的目录即KID，是内核源代码目录，调用该目录顶层下的Makefile,目标为modules。
    M=$(shell pwd)选项让该Makefile在构造modules目标之前返回到模块源代码目录并在当前目录生成obj-m指定的hello.o目标模块。
## make 

## adb push hello.ko /data/

## insmod hello.ko

## cat /proc/kmsg

## rmmod hello.ko
