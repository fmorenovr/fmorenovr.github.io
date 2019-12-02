---
layout: post
title:  "Playing in Ubuntu with different Desktop Environments"
date:   2017-03-02 10:52:56 -0500

tags:
  - Operating systems
  - Ubuntu
  - Desktop Environment
  - LXDE
  - Unity
  - XFCE
  - MATE
  - GNOME

categories:
  - Operating-Systems
---

Here I'll show you different desktop environments for Ubuntu OS.

# Desktop environments

Different Desktops environments for Ubuntu 16.04.2 LTS OS.  
You can see the memory RAM consumed for each Desktop Environment.

## Ubuntu + Unity

Unity is the desktop environment by default for ubuntu OS.

![Ubuntu](/assets/desktopEnvironments/Ubuntu-unity.png "Ubuntu")

## Lubuntu = Ubuntu + LXDE

Lubuntu is an OS Ubuntu derivative with LXDE desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing LXDE:

      sudo apt-get update
      sudo apt-get install lxde

* Result:

![Xubuntu](/assets/desktopEnvironments/Lubuntu-lxde.png "Lubuntu")

## Kubuntu = Ubuntu + KDE

Kubuntu is an OS Ubuntu derivative with KDE desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing KDE:

      sudo add-apt-repository ppa:kubuntu-ppa/backports
      sudo apt-get update
      sudo apt-get install kubuntu-desktop

* Result:

![Kubuntu](/assets/desktopEnvironments/Kubuntu-kde.png "Kubuntu")

## Xubuntu = Ubuntu + XFCE

Xubuntu is an OS Ubuntu derivative with XFCE desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing XFCE:

      sudo apt-get update
      sudo apt-get install xfce4 xfce4-goodies

* Result:

![Xubuntu](/assets/desktopEnvironments/Xubuntu-xfce.png "Xubuntu")

## Ubuntu MATE = Ubuntu + MATE

Ubuntu MATE is an OS Ubuntu derivative with MATE desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing MATE Desktop environment:

      sudo apt-add-repository ppa:ubuntu-mate-dev/xenial-mate
      sudo apt-get update
      sudo apt-get install mate 

* Result:

![Ubuntu_MATE](/assets/desktopEnvironments/Ubuntu_MATE-mate.png "Ubuntu MATE")

## Ubuntu GNOME = Ubuntu + GNOME

Ubuntu GNOME is an OS Ubuntu derivative with GNOME desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing GNOME Desktop environment:

      sudo add-apt-repository ppa:gnome3-team/gnome3-staging
      sudo add-apt-repository ppa:gnome3-team/gnome3
      sudo apt update
      sudo apt install gnome gnome-shell

* Result:

![Ubuntu_GNOME](/assets/desktopEnvironments/Ubuntu_GNOME-gnome.png "Ubuntu GNOME")

## Ubuntu Budgie = Ubuntu + Budgie

Ubuntu Budgie is an OS Ubuntu derivative with Budgie desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing Budgie DE:

      sudo add-apt-repository ppa:budgie-remix/ppa
      sudo apt update
      sudo apt install budgie-desktop-environment

* Result:

![Ubuntu Budgie](/assets/desktopEnvironments/Ubuntu_BUDGIE-budgie.png "Ubuntu Budgie")

## Linux Mint = Ubuntu + Cinnamon

Linux Mint is an OS Ubuntu derivative with Cinnamon desktop environment by default,
but is easily install on Ubuntu and configure the OS.

* Installing Cinnamon Desktop environment:

      sudo add-apt-repository ppa:embrosyn/cinnamon
      sudo apt-get update
      sudo apt-get install cinnamon cinnamon-core

* Result:

![Linux_Mint](/assets/desktopEnvironments/Linux_Mint-Cinnamon.png "Linux Mint")


