---
layout: page
subtitle: "Light Environment Debian based OS"
description: "Configure a Light Environment Debian based OS."
permalink: /pages/light_environment_debian
---
# Light Environment Debian-Ubuntu

Configuration to have a lightweight system.

## Shutdown System

Command to shutdown Linux Debian based OS using bash:

    poweroff

## Console Mode

In the file `/etc/default/grub` modify:

    GRUB_TERMINAL=console
    #GRUB_CMDLINE_LINUX_DEFAULT="quiet"
    #GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    GRUB_CMDLINE_LINUX="text"

* Then, update the grub configuration:

      sudo update-grub

* Changing to text mode:

      sudo systemctl set-default multi-user.target 

* Changing to graphic mode:

      sudo systemctl set-default graphical.target 

* Or in text mode:

      startx

##  Cores temperature

With this you can see the cores temperature.

    sudo apt-get install lm-sensors
    sensors

![sensors][sensors-init]

## Calendar

On the terminal:

    cal -3

![calendar][cal-init]

## Language Keyboard Change

English US, international with dead keys

### setxkbmap

Command to adjust keyboard:

    ls /usr/share/X11/xkb/symbols
    cat /etc/default/keyboard
    sudo setxkbmap -layout "us"
    sudo setxkbmap -layout "us" -variant "intl"

## Shells Manager

### byobu

Multiples bash sessions in only one xsession

    sudo apt-get install byobu

You can see a Byobu guide pressing [here][byobu-guide-url].

## Package Manager

### gdebi-core

Toolkits to install local packages.

    sudo apt-get install gdebi-core
    sudo gdebi packageX.deb

## Disk Manager

### gparted

Helpful to partition disk.

    sudo apt-get install gparted

![gparted][gparted-init]

## Process Managment

### htop

Show all processes in execution on the processors.

    sudo apt-get install htop
    htop

![htop][htop-init]

### gnome-system-monitor

Graphical mode to manage processes:

    gnome-system-monitor

## Network Traffic

### iftop

You can see	how much traffic is interchanged between our host and remot host:

    sudo apt-get install iftop
    sudo iftop -i wlp7s0

![iftop][iftop-init]

### nload

You can see all the traffic in all the interfaces:

    sudo apt-get install nload

![nload][nload-init]

### slurm

You can see all the trafiic on a specific interface with colors:

    sudo apt-get install slurm
    slurm -i wlp7s0

![slurm][slurm-init]

### tcptrack

Tells how much bandwidth is being used and also what protocol (service/port) and destination the transmission is taking place to

    sudo apt-get install tcptrack
    sudo tcptrack -i wlp7s0

![tcptrack][tcptrack-init]

## Compress File

File Compressor, Files.

### 7zip Rar

* Install:

      sudo apt-get install p7zip p7zip-rar rar unrar-free p7zip-full

* Compress folder basic to basic.zip

      7z a basic.7z basic

* Uncompress the file basic.zip

      7z x basic.7z

## Default Applications Modify

### Exo-Utils

* Default application manager.

      sudo apt-get install exo-utils

* Open and modify:

      exo-preferred-applications

### Update-Alternatives

* The default application are:

      gksudo gedit ~/.local/share/applications/mimeapps.list 

* also:

      gksudo gedit /usr/share/applications/defaults.list

* or also:

      sudo update-alternatives --config x-terminal-emulator 

* for the program x-terminal-emulator or for all:

      sudo update-alternatives --all

* or also in GUI:

      gnome-control-center

* or also creating environment variable in `~/.bashrc`:

      export EDITOR="nano"
      export BROWSER="firefox"

* Then, updating:

      sudo update-initramfs -u

## Images Editor

### GIMP

    sudo apt-get install gimp

## Text Editor

### Vim

Similar to nano but with more functions:

    sudo apt-get install vim

![vim-img][vim-init]

You can see a Vim guide pressing [here][vim-guide-url].

## File System Manager

### pcmanfm

    sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
    sudo apt-get update
    sudo apt-get install pcmanfm gvfs

### ranger

* Console file system

      sudo apt-get update
      sudo apt-get install ranger caca-utils highlight atool w3m poppler-utils mediainfo

* Copy the configuration:

      ranger --copy-config=all

  ![ranger][ranger-init]

## Audioplayer

### cmus

* Music mp3 player:

      sudo apt-get install cmus

* Commands:

        :add /dir/path/ to add music from directory
        c to pause or play.
        v to stop.
        x to restart.
        + or - to increase or decrease volumen.
        TAB to change tabs.
        spacebar to open an element's content.
        z previous song.
        b next song.

  ![cmus][cmus-init]

## Videoplayer

### mplayer

    sudo apt-get install mplayer
    mplayer [Filename]

### VLC player

* Music, video, audio player.

      sudo apt-get install vlc vlc-plugin-pulse

* Console mode:

      vlc --intf ncurses [filename]
      cvlc [filename]

* Graphic mode:

      vlc [filename]

  ![vlc][vlc-init]

## Pictures viewer

### gpicview

* Install:

      sudo apt-get install gpicview

* Open an image or open gpicviewer and choose the file to open.

      gpicview /path/to/file/image.jpg

## PDF viewer

### Zathura

* Install:

      sudo apt-get install zathura
      zathura meow.pdf

* To open a file, just write `o`" + tab and look for the path & file.

      ~/Desktop/direxample/Document.pdf

## Web Browsers

### Tor

* Web Browser that use firefox.

      sudo add-apt-repository ppa:webupd8team/tor-browser
      sudo apt-get update
      sudo apt-get install tor-browser

###  Links

* Web Browser that doesnt support imagen, videos, just text only.

      sudo apt-get install links links2

* Switch Meaning
    * `-g`  Web browser execute graphic environment.
    * `-mode`	  Set graphic mode.
    * `-driver`	Specifies the graphic system.

* Specification of the colors with 1024x768 and 16 million colours

      links -g -mode 1024x768x16M
      links2 -g www.google.com.pe
      links www.google.com.pe

  ![links][links-init]

### Lynx

    sudo apt-get install lynx

![lynx][lynx-init]

### Flash

* Flash player, helful to see videos, images, etc

      sudo add-apt-repository ppa:nilarimogard/webupd8
      sudo apt-get update
      sudo apt-get install browser-plugin-freshplayer-pepperflash

## Screen Shot

### shutter

* Console screenshoter

      sudo add-apt-repository ppa:shutter/ppa
      sudo apt-get update
      sudo apt-get install shutter

* Full screen with a specific filename and is saved in our actual directory.

      shutter -f -o shot.png

* Full screen with a non-specific filename (by default is the timedate) and is saved on Pictures directory.

      shutter -f

* Area screen, specifying file:

      shutter -s -o meow.png

* Area screen

      shutter -s

### ksnapshot

    sudo apt-get install ksnapshot
    ksnapshot

## Screen brightness

### xblacklight

* Install:

      sudo apt-get install xbacklight

* Increases brightness by 10%

      xbacklight -inc 10

* Decreases brightness by 10%

      xbacklight -dec 10

* Set brightness in 80%

      xbacklight -set 80

* Or more easily:

    * Decreases by 10:

          xbacklight -10.

    * Increase by 10:

          xbacklight +10

## Sound Controller

### alsamixer

* Console mode - On/Off:

      amixer -D pulse sset Master toggle

* Modify the audio called 'Master':

      amixer -D pulse sset Master 5%-

* Graphic mode:

      alsamixer

  Press F6 and choose PCH instead HDMI (projector sound audio) and modify `Master`.

  ![alsamixer][alsamixer-init]

## Screen Background

### nitrogen

    sudo apt-get install nitrogen
    nitrogen --set-centered /path/.i3/DragonInferno.jpg
    nitrogen --set-scaled /path/.i3/DragonInferno.jpg

## Network Manager

### nmap

* Helful to detect all devices connected on your network.

      sudo apt-get install nmap
      sudo nmap -sP 192.168.20.0/24

* Graphic mode:

      sudo apt-get install netdiscover

* Ethernet:

      sudo netdiscover -r 192.168.1.0/24

* Wireless:

      sudo netdiscover -r 192.168.1.0/24 -i wlan0

  ![nmap][nmap-init]

### nmcli

    nm-connection-editor 

* Graphic mode:

      nm-applet

* Connecting to a wireless net:

      sudo nmcli dev wifi connect "netname" password "passwd"

* Disconnect:

       sudo nmcli dev disconnect iface eth0

* Show enabled devices:

      sudo nmcli dev

* Turn off/on wifi:

      sudo nmcli r wifi off/on

## Network Configiguration

### wlan0/eth0 configuration

Types of security: Open/WEP/WPA/WPA2

* Enabled/disabled the wireless/ethernet card:

      sudo ifconfig wlan0 up/down
      sudo ifconfig eth0 up/down

* Look for a network to connect:

      iwlist wlan0 scan

* Connect to a network:

    * Security Open:

          sudo iwconfig essid "netname"

    * Security WEP:

          sudo iwconfig essid "netname" key ["HExadecimal_Clave_red"  o "s:decimal_key"]

* Renews the dynamically-assigned IP address of a interface ethernet/wireless device.

      sudo dhclient wlan0
      sudo dhclient eth0

### Interfaces configuration

* Show all network configurations:

      sudo nano /etc/network/interfaces

* Dynamic (through dhclient)

      auto wlan0
      iface wlan0 inet dhcp
      wireless-essid netname
      wireless-key passwd
      wireless-mode managed
      
      auto eth0
      iface eth0 inet dhcp

* Static

      auto wlan0
      iface wlan0 inet static
      wireless-essid netname
      wireless-key passwd
      wireless-mode managed
      address 192.168.100.150
      netmask 255.255.255.0
      network 192.168.100.0
      gateway 192.168.100.1
      broadcast 192.168.100.255
      dns-nameservers 8.8.8.8 8.8.4.4
      
      auto eth0
      iface eth0 inet static
      address 192.168.100.15
      netmask 255.255.255.0
      network 192.168.100.0
      gateway 192.168.100.1
      broadcast 192.168.100.255
      dns-nameservers 8.8.8.8 8.8.4.4
    
* Then, restart the service:

      sudo /etc/init.d/networking restart

### DNS configuration

* List DNS servers for internet domain name resolution.

      cat /etc/resolv.conf

* Result:

      nameserver 8.8.8.8
      nameserver 8.8.4.4

### Hosts Configuration

* Show Ip and hostsname asociated, we can add another hosts.

      cat /etc/hosts

* Show our hostname, we can change our hostname.

      cat /etc/hostname

* Show network interfaces:

      ls /sys/class/net

* eth0:  ethernet
* lo:    local loop
* wlan0: wireless

## Booteable USB

* Terminal:

      sudo dd if=[path_to_iso] of=[path_to_usb]
      sudo dd if=~/Downloads/debian-7.4.0-amd64-CD-1.iso of=/dev/sdb

* Graphical mode with `Disk Creator`.



[vim-guide-url]:   /blog/text_editors/2017-05-05/A-Fast-Guide-for-Newcomers-to-Vim
[byobu-guide-url]: /blog/shell_terminals/2017-05-05/A-Fast-Guide-for-Newcomers-to-Byobu


[alsamixer-init]:    /assets/systemCommand/alsamixer/alsamixer.png
[cal-init]:          /assets/systemCommand/calendar/calendar.png
[cmus-init]:         /assets/systemCommand/cmus/cmus.png
[gparted-init]:      /assets/systemCommand/gparted/gparted.png
[htop-init]:         /assets/systemCommand/htop/htop.png
[iftop-init]:        /assets/systemCommand/iftop/iftop.png
[links-init]:         /assets/systemCommand/links/links.png
[lynx-init]:         /assets/systemCommand/lynx/lynx.png
[netdiscover-init]:	 /assets/systemCommand/netdiscover/netdiscover.png
[nload-init]:        /assets/systemCommand/nload/nload.png
[nmap-init]:         /assets/systemCommand/nmap/nmap.png
[ranger-init]:       /assets/systemCommand/ranger/ranger.png
[sensors-init]:      /assets/systemCommand/sensors/sensors.png
[slurm-init]:        /assets/systemCommand/slurm/slurm.png
[tcptrack-init]:     /assets/systemCommand/tcptrack/tcptrack.png
[vlc-init]:          /assets/systemCommand/vlc/vlc.png
[vim-init]:          /assets/textEditor/vim/vim_init.png

