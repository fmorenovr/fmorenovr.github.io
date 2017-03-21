---
layout: page
subtitle: "Deepin 15.3 networking"
description: "configure /etc/network/interfaces file"
permalink: /pages/deepin_networking
---
### Deepin 15.3 VM

* First, installing components:

      sudo apt-get update
      sudo apt-get install lsb-core htop

* Configure the network interfaces:

      sudo nano /etc/network/interfaces

* Add or modify:

      auto ens3
      iface ens3 inet static
      address 192.168.100.132
      netmask 255.255.255.0
      network 192.168.100.0
      gateway 192.168.100.1
      broadcast 192.168.100.255
      dns-nameservers 8.8.8.8 8.8.4.4

* Restart the services:

      sudo /etc/init.d/networking restart

* Now, we connect from the OS host through ssh:

      ssh jenazad@192.168.100.132


