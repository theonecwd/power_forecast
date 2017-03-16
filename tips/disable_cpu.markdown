# 禁用cpu core
```bash
adb root
#adb remount
adb shell stop mpdecision
echo "0" > /sys/devices/system/cpu/cpu1/online
echo "0" > /sys/devices/system/cpu/cpu2/online
echo "0" > /sys/devices/system/cpu/cpu3/online
```

```
$ adb root
$ adb remount
$ adb shell stop mpdecision
$ adb shell mv /system/bin/mpdecision /system/bin/mpdecision-rm
 
// To re-enable MP decision
$ adb root
$ adb remount
$ adb shell mv /system/bin/mpdecision-rm /system/bin/mpdecision
$ adb shell start mpdecision
```
