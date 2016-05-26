# compile goldfish
```
cd goldfish 
make goldfish_armv7_defconfig 默然编译选项,执行后会生成.config文件
更多现有的config文件在arch/arm/configs
make -j4
运行emulator 使用编译好的内核goldfish/arch/arm/boot/zImage
可以运行make menuconfig 配置编译选项
```
