# 固定cpu频率
>  If you have selected the "userspace" governor which allows you toset the CPU operating frequency to a specific value, you can read 
out the current frequency in scaling_setspeed. By "echoing" a new frequency into this you can change the speed of the CPU, but only within the limits of  scaling_min_freq and scaling_max_freq.



```bash
cd /sys/devices/system/cpu/cpu0/cpufreq/cpu0/
cat scaling_available_governors
cat scaling_available_frequencies
echo userspace> scaling_governor

#echo xxxx > scaling_cur_freq 这种方法是不行的。

echo xxxx> scaling_setspeed这种方法也是可行的。

adb shell "echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
adb shell "echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"
adb shell "echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq"
```
https://gist.github.com/clvv/523789


