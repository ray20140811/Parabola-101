configure xterm
===============
[Have a black background by default](https://makandracards.com/makandra/8057-xterm-have-a-black-background-by-default)

create .Xresources and change color
-------------------

   [ray@Parabola ~]$ vim ~/.Xresources
   xterm*background: black
   xterm*foreground: lightgray
   [ray@Parabola ~]$ xrdb ~/.Xresources
   
change Font Size
-------------------

   [ray@Parabola ~]$ vim ~/.Xresources
   xterm*faceName: monospace:pixelsize=16
   
   
