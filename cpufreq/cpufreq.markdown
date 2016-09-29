# Cpufreq
## CPU 电源状态（C State）和 CPU/设备性能状态（P State）
在开始 CPUfreq 讨论之前，我们先来看看 CPU 电源状态和 CPU/设备性能状态。
### CPU 电源状态：几乎全是空闲

CPU 电源状态（不包括处理器运行时的 C0 状态）是空闲状态，处理器将解锁并关闭组件来节省电能。CPU 电源状态程度越深，采取的电能节省措施就越多 — 比如说停止处理器时钟或停止外部中断请求。这些状
态帮助空闲中的系统节省电能。

此外，C1E 模式（或称作 Enhanced C1 或 C1 Enhanced Mode）也可以帮助空闲系统节省电能。同样通过降低电压和频率，C1E 尝试比传统 C1 状态（只会停止时钟信号）提供更大的电能节省。事实上，C1E 能够
比任何 CPUfreq 调控器更快地降低电压/频率。

并非所有处理器都有这些选项，但是要使用 C 电源状态和 CIE，请确保启用了 BIOS 选项 CPU C State 和 C1E（或者类似的选项），以便于在空闲时实现更大的电能节省。一些系统支持 C3 甚至 C6 尝试休眠状
态。

记住，CPU 电源状态程度越深，节省的电能就越多。 






![test](../pic/cpufreq_state.gif)

[参考](https://www.ibm.com/developerworks/cn/linux/l-cpufreq-1/#resources)
[Documentf翻译](http://blog.csdn.net/ganggexiongqi/article/details/7368781)

