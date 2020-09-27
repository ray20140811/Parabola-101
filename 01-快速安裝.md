 Parabola GNU/Linux-Libre 快速安裝指南
=======================
本文參考自 [Arch Linux 快速安裝指南](https://gist.github.com/bcbcarl/5d3d9c41d728eef395dd).
主旨在介紹 Parabola GNU/Linux-Libre 安裝流程，必須連接網路，細部設定請參考 [Parabola Wiki](https://wiki.parabola.nu/Installation_Guide)

建立 GPT 分割磁區
-----------------
使用 gdisk 可以建立 GPT 分割磁區：

    [root@parabolaiso ~]# gdisk /dev/sda

參考設定簡述如下，可自行修改設定多個分割區：

    o, y                                    # 建立新的分割表
    n, 1, (default), +2M, ef02              # BIOS 開機磁區 (/dev/sda1)
    n, 2, (default), (default), (default)   # 其餘空間分配給系統 (/dev/sda2)
    p                                       # 確認分割表無誤(可略過此步驟)
    w, y                                    # 分割表正確則寫入

詳細步驟如下:

    Command (? for help): o
    This option deletes all partitions and creates a new protective MBR.
    Proceed? (Y/N): y

    Command (? for help): n
    Partition number (1-128, default 1): 1
    First sector (34-20971486, default = 2048) or {+-}size{KMGTP} :
    Last sector (2048-20971486, default = 20971486) or {+-}size{KMGTP}: +2M
    Current type is 8300 (Linux filesystem)
    Hex code or GUID (L to show codes, Enter = 8300): ef02
    Changed type of partition to 'BIOS boot partition'

    Command (? for help): n
    Partition number (1-128, default 1): 2
    First sector (34-20971486, default = 6144) or {+-}size{KMGTP} :
    Last sector (2048-20971486, default = 20971486) or {+-}size{KMGTP}:
    Current type is 8300 (Linux filesystem)
    Hex code or GUID (L to show codes, Enter = 8300):
    Changed type of partition to 'Linux filesystem'

    Command (? for help): w

    Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING PARTITIONS!!

    Do you want to proceed? (Y/N): y
    OK; writing new GUID parition table (GPT) to /dev/sda.
    The operation has completed successfully.

格式化磁區
----------
分割完成後，建立檔案系統：

    [root@parabolaiso ~]# mkfs.ext4 /dev/sda2    # 建立 ext4 檔案系統

掛載系統
--------
    [root@parabolaiso ~]# mount /dev/sda2 /mnt    # 預設掛到 /mnt 目錄

安裝系統
--------
    [root@parabolaiso ~]# pacstrap /mnt base

安裝Kernel
--------
    [root@parabolaiso ~]# pacstrap /mnt linux-libre-lts

安裝網路管理員
--------    
    [root@parabolaiso ~]# pacstrap /mnt networkmanager    

安裝parabola-base工具包
--------    
parabola-base有許多實用工具,例如:nano/vi編輯器,man,mc等,建議安裝.
(若不安裝,安裝完進入系統會沒有編輯器可用)

    [root@parabolaiso ~]# pacstrap /mnt parabola-base           

安裝bootloader
--------
    [root@parabolaiso ~]# pacstrap /mnt grub

設定系統
--------
    [root@parabolaiso ~]# genfstab -p /mnt >> /mnt/etc/fstab
    [root@parabolaiso ~]# arch-chroot /mnt                  

    # 進入系統
    [root@parabolaiso /]# echo Parabola > /etc/hostname     # 設定Host Name. Parabola 可以換成你要的名稱
    [root@parabolaiso /]# ln -s /usr/share/zoneinfo/Asia/Taipei /etc/localtime    # 設定系統時區
    [root@parabolaiso /]# passwd                            # 設定 root 密碼
    [root@parabolaiso /]# USERNAME='Bill'                   # 設定 user
    [root@parabolaiso /]# useradd -m $USERNAME              
    [root@parabolaiso /]# passwd $USERNAME      

    # 以下步驟非必須
    [root@parabolaiso /]# vi /etc/locale.gen           # 啟用 en_US.UTF-8、zh_CN.UTF-8 以及 zh_TW.UTF-8
    [root@parabolaiso /]# locale-gen    # 產生中英文語系
    [root@parabolaiso /]# vi /etc/locale.conf    # 設定系統語系
    LANG="en_US.UTF-8"
    LC_COLLATE="C"
    [root@parabolaiso /]# export LANG="en_US.UTF-8"    # 立即生效
    [root@parabolaiso /]# hwclock --systohc --utc    # 設定硬體時鐘為 UTC

開機管理程式
------------
    [root@parabolaiso /]# grub-install /dev/sda
    [root@parabolaiso /]# grub-mkconfig -o /boot/grub/grub.cfg

退出安裝
--------
    [root@parabolaiso /]# exit
    [root@parabolaiso ~]# umount /mnt
    [root@parabolaiso ~]# reboot    # 退出安裝媒體後重新開機

桌面環境
--------
請參考[桌面環境設定](/2d4c77cc06955f74bd0b "Parabola Linux 桌面環境設定")一文。
