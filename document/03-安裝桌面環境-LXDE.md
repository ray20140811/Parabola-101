
Parabola GNU/Linux-Libre 安裝桌面環境
=======================
本文參考
[Arch Linux：安裝圖形界面(X)](http://www.wlintmp.net/2014/02/arch-linux_8.html)

安裝xorg
----------

    [root@Parabola ~]# pacman -S xorg    

安裝啟動工具
----------
    [root@Parabola ~]# pacman -S xorg-xinit

安裝lxde
----------
    [root@Parabola ~]# pacman -S lxde

啟動設定
----------
在~/.xinitrc加上exec startlxde

    [root@Parabola ~]# vi ~/.xinitrc
    exec startlxde

啟動桌面
----------
    [root@Parabola ~]# startx
   
lxde調整解析度
----------
    [root@Parabola ~]# xrandr -s 1024x768
