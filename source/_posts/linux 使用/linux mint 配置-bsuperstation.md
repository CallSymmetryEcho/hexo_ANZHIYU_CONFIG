---
title: Linux Mint 配置 - Bsuperstation
date: 2024-02-21 00:00:00
tags:
  - Linux
  - 配置
---

# Linux Mint 配置 #整理

- zsh
- appimageluncher
- cmake 3.27

```
# download source form git lab然后
./bootstrap
make -j12
make install
```

- kde PLASMA 桌面安装
- latte --》 仿mac os启动器
- Panel Transparency Button --> 把边栏变透明
- reclone --> 挂载云端硬盘
- google-drive-ocamlfuse --> 挂载google_dirve https://github.com/astrada/google-drive-ocamlfuse
-  如果报某个库 ld.so 有错误，估计就是安装时安错了，重新下载符合版本要求的再安一次，如appimageluncher
-
-----
KDE 使用遇到wifi问题

- 没有wifi控制：
~~~ bash
apt install plasma-nm
~~~
然后可以在setting看到

此时已经断网，使用命令行控制
~~~bash
nmcil r wifi on #打开wifi
nmcil dev wifi
nmcil dev wifi connect "wifi名" password "passwd"
~~~

- 安装 touchegg 能让linux 拥有众多的触控板手势
https://github.com/JoseExposito/touchegg
- 使用了 flathub  -> flatpak install
- https://flathub.org/
- 增加了emote,使用 CTRL+SHIFT+E 调用
- https://github.com/tom-james-watson/Emote