---
title: Linux mint 21.3 更新 kernel 6.5 使用 coolercontrol 和 liquidctl 解决 Corsair 150i LCD 冷排风扇问题
date: 2024-01-10 00:00:00
tags:
  - Linux
  - 冷排
  - Corsair
---

# Linux Mint 21.3 Kernel 更新与冷排驱动问题

> 问题描述，问题其实很有意思，就是冷排的驱动无法被linux读取到因为使用的是cosair commander ST, usb连接

- Step1 需要更新kernel 20240110 我更新6.5.0是可以用的
- Step2安装Liquidctl https://github.com/liquidctl/liquidctl
	- 根据它给的步骤来就行，安装好后需要给系统加rules：
~~~SHELL
echo 'KERNEL=="uinput", SUBSYSTEM=="misc", OPTIONS+="static_node=uinput", T  
AG+="uaccess"' | \  
sudo cp ./71-liquidctl.rules /etc/udev/rules.d/71-liquidctl.rules
#rules的路径在liquidctl文件夹中/extra/linux/目录下 
~~~
更新一下rules
~~~shell
sudo udevadm control --reload-rules && sudo udevadm trigger
~~~ 

这个时候就可以使用liquidctl去是用命令行控制了

--- 也可以使用 GUI：coolercontrol: https://gitlab.com/coolercontrol/coolercontrol/-/tree/main

