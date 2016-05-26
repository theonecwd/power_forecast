# hello world
cd goldfish/drivers
mkdir hello

## ./hello/hello.c
touch ./hello/hello.c
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
## ./hello/Makefile
touch ./hello/Makefile
```makefile
#可选模块
obj-$(CONFIG_HELLO) += hello.o  

#内建模块
#obj-y := hello.o
```

## ./hello/Kconfig
touch ./hello/Kconfig
```konfig
config HELLO 
    tristate "Fake Register Driver"
    default n
    help
    This is the freg driver for android system.
```

## ./Kconfig
```
source "drivers/hello/Kconfig"
```

## ./Makefile
```
obj-$(CONFIG_HELLO)+=hello/
```

## make menuconfig 的时候把该项选上,然后make
也可以在hello/Makefile中 obj-y := hello.o,此时hello/Kconfig可以为空,
.Makefile中obj-y+=hello/ .Kconfig为空,这种配置方法默认是编译进内核的


