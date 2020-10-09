Parabola GNU/Linux-Libre 網路設定
=======================

本文參考 
1. [arch linux Network Configuration](https://wiki.archlinux.org/index.php/Network_configuration_(%E6%AD%A3%E9%AB%94%E4%B8%AD%E6%96%87)) 
2. [Arch Linux：設定網路](http://www.wlintmp.net/2015/11/arch-linux.html)
3. [Arch Linux SSH Server Setup, Customization and Optimization](https://linuxhint.com/arch_linux_ssh_server/)

檢查連線
----------

    [root@Parabola ~]# ping -c 3 8.8.8.8    # 出現ping: connect: Network is unreachable表示網路有問題

列出所有可用的界面(interface)
----------
ip link 和 ls /sys/class/net 功能相同,都是列出所有可用的介面

    [root@Parabola ~]# ip link
    enp0s3 lo

    [root@Parabola ~]# ls /sys/class/net
    enp0s3 lo

顯示網路界面(interface)詳細內容
----------
    [root@Parabola ~]# ip addr

啟用網路界面
----------
    [root@Parabola ~]# ip link set enp0s3 up

動態IP
----------
啟動DHCP:

    [root@Parabola ~]# systemctl start dhcpcd@enp0s3

設定開機會自動啟動DHCP:

    [root@Parabola ~]# systemctl enable dhcpcd@enp0s3

設定DNS
----------
編輯/etc/resolv.conf:

    [root@Parabola ~]# vi /etc/resolv.conf    

加上DNS Server:

    nameserver 8.8.4.4
    nameserver 8.8.8.8

重啟服務:

    [root@Parabola ~]# systemctl start systemd-networkd.service

網路校時
----------
安裝 ntp 軟體包：

    [root@Parabola ~]# pacman -S ntp 

執行校時：    

    [root@Parabola ~]# ntpdate time.stdtime.gov.tw

可用的 NTP 伺服器如下：

    * tock.stdtime.gov.tw
    * watch.stdtime.gov.tw
    * time.stdtime.gov.tw
    * clock.stdtime.gov.tw
    * tick.stdtime.gov.tw

安裝SSH Server
----------
更新:

    [root@Parabola ~]# pacman -Sy

安裝 OpenSSH Server 軟體包：

    [root@Parabola ~]# pacman -S openssh

啟動 SSH Server：    

    [root@Parabola ~]# systemctl start sshd    

檢視 SSH Server狀態：    

    [root@Parabola ~]# systemctl status sshd

設定開機自動啟動 SSH Server：    

    [root@Parabola ~]# systemctl enable sshd     

查詢IP:

    [root@Parabola ~]# ip a
