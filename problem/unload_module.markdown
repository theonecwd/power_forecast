# unload module
## delete\_module failed (errno 38)

这个问题主要是没有配置模块卸载
解决办法如下：
```
make menuconfig
enter enable loadable module support and select module unloading
```


