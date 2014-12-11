#stm8_wl315

----------

##1 介绍
一个基于stm8单片机的315M无线模块

##2 特性
1) 占用资源少，只需要一个GPIO，一个定时器；

2）能够很好地嵌入到其他应用中，完全基于状态机；

3）具有控制器学习功能；

4）基于官方驱动库；

5）使用便宜的315M无线模块；

6）核心为高性价比的stm8单片机，不但本身可以作为一个微型系统扩展其他功能，也可以作为模块与树莓派等硬件通信（uart或spi）。你也可以移植到别的单片机。

##3 功能说明
###1）数据解码

1.数据解码程序运行在定时器中断，由于是状态机所以消耗很短时间。获取到有效数据会通过宏WLSTA\_SET\_RNE()将全局变量g\_chWlStatus的RNE置位;

2.wl315\_learn\_task（）的LEARN\_WAIT状态中wl315\_get\_data()会确保收到两次相同数据才返回有效数据。


###2）按键学习

1.目前程序提供四个按键学习功能，可以继续扩充；

2.学习方法

I.按下按键不放，等到LED闪一下（两下，三下...），松手；

II.现在LED会快闪一下（两下，三下...），表明是学习状态，而且快闪次数就是所学按键的序号；

III.用遥控器发送信号，LED停止闪烁，表明学习完成。

**注意：**

1.对于不同的控制器，模块的定时器初始化和常量MAX\_CODE\_CNT, MIN\_SYN\_CNT, MAX\_SYN\_CNT可能有差异，请明白程序原理后再作出修改。
2.需要官方标准外设库，请到st官网获取。

##4 补充
提供一个原理图的参考（目前的原理图忘了加学习按键，以后重新用Kicad画一版）。




