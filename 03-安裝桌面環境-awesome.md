
Parabola GNU/Linux-Libre 安裝桌面環境
=======================
本文參考
[Arch Linux Wiki：awesome)](https://wiki.archlinux.org/index.php/Awesome_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#%E5%AE%89%E8%A3%85)

安裝xorg
----------

    [root@Parabola ~]# pacman -S xorg    

安裝啟動工具
----------
    [root@Parabola ~]# pacman -S xorg-xinit

安裝lxde
----------
    [root@Parabola ~]# pacman -S awesome

啟動設定
----------
在~/.xinitrc加上exec awesome

    [root@Parabola ~]# vi ~/.xinitrc
    exec awesome

啟動桌面
----------
    [root@Parabola ~]# startx
