AltYo
=====

AltYo - drop-down terminal emulator, written in vala, depends only on libvte and gtk3.

Main program advantages.
------------------------
* Design of altyo allow open unlimited tab count, even with long terminal title.  
     if tabs  not fit in the row, they move to a new line.
* Drag and drop tabs.
* Tabs does not stand out from the terminal.(solid view)
* Title of the tabs fully customisable.  
     You can highlight parts of the terminal header by color (for example, highlight username and hostname)  
     You can adjust the header of the terminal, using regular expressions(for example cut unnecessary parts).
* Autostart with desktop session.
* Autostart programs,for example, start mocp and mutt in new tabs by default.
* Program will warn you if you try to close the terminal with an important program(ssh,wget pattern is customizable), even if program runned in the background.
* Delayed "Close tab", you have 10 seconds before tab will actually closed, so if you change your mind, press `<Ctrl><Shift>R` to restore tab, also you may restore tab from terminal popup menu.
* You may "Lock" important tab, program will ask you to confirm close tab. ("Lock tab" is available from context menu on tab button)
* All options can be configured via graphical settings dialog.
* Program will warn you if you setup incorrect setting value, if settings is absent in config file, program will use default value.
* Hotkey for ~~the first 20~~ unlimited tabs (double press of `alt+5` will switch to 15 tab, triple press will switch to 25 tab and so on)
* You may use css to styling program (thanks to gtk3)
* Multi monitor support.  
  * You can setup, on which monitor start by default.  
  * Individual window size and position for each monitor.
  * Program have mode "Follow the mouse", in this mode, after hiding, window will shown on same monitor with mouse pointer.
* Tiling window manager support (usual window).  
     Use `--standalone` command line option to run in tiling window manager,  
     For any other window managers, altyo will operate as usual terminal emulator (like xterm).
* Multiple instances. You may run several instances of alto in same time.  
  To do that you should setup unique id for each instance and use separate configuration file.  
  For example:  
  `altyo --id=org.gtk.altyo_left_monitor -c ~/.config/altyo/config_left_monitor.ini`  
  `altyo --id=org.gtk.altyo_right_monitor -c ~/.config/altyo/config_right_monitor.ini`  
  now you may control each instance individually  
  `altyo --id=org.gtk.altyo_left_monitor -e "htop"`  
  `altyo --id=org.gtk.altyo_right_monitor -e "mc"`  
  If you don't want invent unique id, you may use `--id=none`, but in that case you will have no possibility to control instances from command line.

[![Main window](http://storage6.static.itmages.ru/i/13/0406/s_1365230653_4853839_d41d8cd98f.png)](http://itmages.ru/image/view/971951/d41d8cd9)
[![Preferences Look and feel](http://storage3.static.itmages.ru/i/13/0406/s_1365229810_3352986_d41d8cd98f.png)](http://itmages.ru/image/view/971932/d41d8cd9)
[![Preferences Key bindings](http://storage5.static.itmages.ru/i/13/0406/s_1365229912_4764716_d41d8cd98f.png)](http://itmages.ru/image/view/971933/d41d8cd9)
[![Preferences Advanced](http://storage6.static.itmages.ru/i/13/0406/s_1365229959_4473970_d41d8cd98f.png)](http://itmages.ru/image/view/971934/d41d8cd9)
[![Tiling window manager](http://storage3.static.itmages.ru/i/13/0612/s_1371022015_7777413_5cf29d0faf.png)](http://itmages.ru/image/view/1071250/5cf29d0f)
[![Tiling window manager](http://storage5.static.itmages.ru/i/13/0612/s_1371022059_3043913_a19d77ddef.png)](http://itmages.ru/image/view/1071252/a19d77dd)
[![Normal window](http://storage2.static.itmages.ru/i/13/0612/s_1371037750_9206122_f69d88b067.png)](http://itmages.ru/image/view/1071578/f69d88b0)

small video presentation of available features:
* youtube video altyo 0.3  
  [![youtube altyo 0.3](http://img.youtube.com/vi/IEabsuFresk/0.jpg)](http://youtu.be/IEabsuFresk)
* altyo 0.2 http://youtu.be/9W8m6T7HyVs and http://youtu.be/utxeh-SBTvI

Installing
----
Packages for *Ubuntu and Debian* available there https://launchpad.net/~linvinus/+archive/altyo  
Package for *Arch Linux* AUR https://aur.archlinux.org/packages/altyo-git/ (package created by willemw)

Source code available there https://github.com/linvinus/AltYo  
How to install from sources is described in INSTALL file.

Tips and tricks:
----
1. You always may open new stand-alone terminal, in current directory, by pressing `<Ctrl><Shift>N` (default key binding)
2. In search mode (when text entry have a focus), you may use following hotkeys  
   `ctrl+1` - toggle "Wrap search"  
   `ctrl+2` - toggle "Match case-sensitive"  
   `ctrl+3` - toggle search mode "terminal text"/"terminals titles"  
   `ctrl+Up` or `Enter` - find next  
   `ctrl+Down` - find prev  
   `Up` - search history  
   `Down` - search history  
   `Esc` - close search dialog  
sorry, this keys is hardcoded.
3. You may switching to tab by searching in a titles.  
   To do that you need to open search dialog `<Ctrl><Shift>F` (default key binding),  
   then activate search option  "terminals titles", by pressing `<Ctrl+3>`,  
   then type sought-for part of tab title.  
   Then you may use hotkeys to cycle through the search results  
   `ctrl+Up` or `Enter` - find next  
   `ctrl+Down` - find prev  
   Also, you may configure special hotkey to quickly activate this mode "Search in terminals titles"
4. You may sort tabs by hostname (if tab title contain host name in the following form `<user>@<host>:<path>`)  
   To do that press right mouse button on tab title, then, in context menu, select "Sort by hostname"  
   Also, you may configure special hotkey for this action "Sort by hostname".
5. Altyo is portable, you may copy executable file on your USB flash drive.  
   All you need to run on target machine is installed Gtk 3.4 or newer and libvte 3.0 or newer.  
   This libraries should be available on fresh distributives.
6. Double click on empty space in tab bar will open new tab.
7. Middle click on tab button will close tab.

FAQ:
----
* Q) ubuntu "global menu" + alt+grave
     "global menu" show application menu, when user press alt+grave, but it should not
* A) disable gtk3 auto mnemonics
```
     dconf write /org/gnome/desktop/interface/automatic-mnemonics false
```

* Q) when resizing terminal, lines break, if you are running Zsh
* A) bug is described there https://bbs.archlinux.org/viewtopic.php?pid=1246865
  you need to apply patch (https://bbs.archlinux.org/viewtopic.php?pid=1246865#p1246865).
  to resolve that.
  for ubuntu users, patched vte available in this ppa https://launchpad.net/~linvinus/+archive/vte

* Q) Window gravity south, not working under xfwm4
* A) it is xfwm4 bug https://bugzilla.xfce.org/show_bug.cgi?id=3634

* Q) tabs does not close after entering "exit" command (mc restarting after pressing F10 if it was runned as autorun command)
* A) if you prefer close tabs by "exit" command, you may turn off option "Auto restart shell"

* Q) "auto run" commands doesn't see environment variables from bashrc file
* A) this happen because they are running as standalone application,  
     but, for example, you may use following wrap around `bash -c "EDITOR=vim mc"`  
     in this example mc will runned with special environment variable

Reviews about AltYo
-------------------
zenway.ru (Russian) http://zenway.ru/page/altyo  
muhas.ru (Russian) http://muhas.ru/?p=202
