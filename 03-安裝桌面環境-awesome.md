
Parabola GNU/Linux-Libre 安裝桌面環境
=======================
本文參考
[Arch Linux Wiki：awesome)](https://wiki.archlinux.org/index.php/Awesome_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#%E5%AE%89%E8%A3%85)
[Arch Linux User:How to install& configuring Awesome](https://www.archlinuxuser.com/2013/05/how-to-install-configuring-awesome.html)

安裝xorg
----------

    [root@Parabola ~]# pacman -S xorg    

安裝啟動工具
----------
    [root@Parabola ~]# pacman -S xorg-xinit

安裝awesome
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
    
啟動terminal
----------
    Super[Windows Key] + R: lxterminal 

啟動emacs
----------
    Super[Windows Key] + R: emacs 

awesome default terminal: xterm
----------
安裝xterm就可以用Menu開啟terminal
    
    [root@Parabola ~]# pacman -S xterm
 
    

