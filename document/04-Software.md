Parabola GNU/Linux-Libre 軟體
=======================
本文參考
[Parabola Wiki List of Applications](https://wiki.parabola.nu/List_of_Applications)

新增使用者
----------

    [root@Parabola ~]# pacman -S sudo
    [root@Parabola ~]# useradd -m -G wheel -s /bin/bash bill    # bill 改成你的使用者 
    [root@Parabola ~]# passwd bill    # bill 改成你的使用者
    [root@Parabola ~]# visudo
    root ALL=(ALL) ALL
    bill ALL=(ALL) ALL

apm
----------
apm

    [root@Parabola ~]# pacman -S apm

terminal
----------
xterm
    
    [root@Parabola !]# pacman -S xterm


文字編輯器
----------
* emacs

    [root@Parabola ~]# pacman -S emacs
    
* vim

  [root@Parabola ~]# pacman -S vim

網路瀏覽器
----------
icecat

  [root@Parabola ~]# pacman -S icecat

IRC
----------
* hexchat

  [root@Parabola ~]# pacman -S hexchat
  
git
----------
* git

  [root@Parabola ~]# pacman -S git

arduino IDE
-----------

  [root@Parabola ~]# pacman -S arduino
  [root@Parabola ~]# pacman -S arduino-avr-core
    
