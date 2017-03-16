# battery_walkthrough

```
https://github.com/google/battery-historian
> adb kill-server
> adb devices
> adb shell dumpsys batterystats --reset
<disconnect and play with app>...<reconnect>
> adb devices

>adb shell dumpsys batterystats > batterystats.txt

> python historian.py batterystats.txt > batterystats.html

```

