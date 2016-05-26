# 读写文件
## fiel_operation.c
```c
#include <linux/module.h>
#include <linux/init.h>
#include <linux/fs.h>
#include <linux/uaccess.h>
static char buf[] = "hello";
static char buf1[10];
 
int __init hello_init(void)
{
    struct file *fp;
    mm_segment_t fs;
    loff_t pos;
    printk("hello enter\n");
    fp = filp_open("test_file", O_RDWR | O_CREAT, 0644);
    if (IS_ERR(fp)) {
        printk("create file error\n");
        return -1;
    }
    fs = get_fs();
    set_fs(KERNEL_DS);
    pos = 0;
    vfs_write(fp, buf, sizeof(buf), &pos);
    pos = 0;
    vfs_read(fp, buf1, sizeof(buf), &pos);
    printk("read: %s\n", buf1);
    filp_close(fp, NULL);
    set_fs(fs);
    return 0;
}
void __exit hello_exit(void)
{
    printk("hello exit\n");
}
 
module_init(hello_init);
module_exit(hello_exit);
 
MODULE_LICENSE("GPL"); 

```

## Makefile
```
obj-m := file_operation.o

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
## make && adb push && insmod 
