# insufficient permissions for device

## 设置usb权限
```bash
$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 002 Device 004: ID 24ae:2000  
Bus 002 Device 006: ID 2a45:0c02 Meizu Corp. MX Phone (MTP & ADB)
```

```bash
vim /etc/udev/rules.d/70-android.rules
加入下面的内容
SUBSYSTEM=="usb",ATTRS{idVendor}=="2a45",ATTRS{idProduct}=="0c02",MODE="0666"
```
>  get idVendor and idProduct from output of lsusb


## 重启udev

```bash
ubuntu: service udev restart 
centos: systemctl restart systemd-udev-trigger.service
```

## 重启adb server
```bash
adb kill-server
adb shell
```


