# 固定cpu频率
>  If you have selected the "userspace" governor which allows you toset the CPU operating frequency to a specific value, you can read 
out the current frequency in scaling_setspeed. By "echoing" a new frequency into this you can change the speed of the CPU, but only within the limits of  scaling_min_freq and scaling_max_freq.


```
cd /sys/devices/system/cpu/cpu0/cpufreq/cpu0/
cat scaling_available_governors
cat scaling_available_frequencies
echo userspace scaling_governor
echo xxxx > scaling_cur_freq
```


