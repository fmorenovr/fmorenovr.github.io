---
layout: post
title:  "Virtual Machines Network Configuration"
date:   2017-03-10 14:58:05 -0500

tags:
  - Network configuration
  - Network Emulator
  - Ubuntu

categories:
  - Networking
---

Here you'll learn to set IPs to your VM.

## Debian based OS

You need to config `/etc/network/interfaces` file.

* First, debian has not `sudo` command, so let install:

      su
      apt-get install sudo
      adduser username sudo

* Second, we add our username on the file `/etc/sudoers`:
    
      su
      nano /etc/sudoers

* Third, add the following line:

      usernamehere  ALL=(ALL:ALL) ALL

* Four, installing components (the last command, in some cases is not necessary):

      sudo apt-get update
      sudo apt-get install lsb-core htop
      sudo cp /sbin/ifconfig /usr/local/bin/

* Configure the network interfaces:

      sudo nano /etc/network/interfaces

* Add or modify:

      auto eth0
      iface eth0 inet static
      address 192.168.100.133
      netmask 255.255.255.0
      network 192.168.100.0
      gateway 192.168.100.1
      broadcast 192.168.100.255
      dns-nameservers 8.8.8.8 8.8.4.4

* Restart the services:

      sudo /etc/init.d/networking restart
      sudo systemctl start sshd.service
    
* Now, we connect from the OS host through ssh:

      ssh jenazad@192.168.100.133


## Red Hat Enterprise Linux based OS

You need to config `/etc/sysconfig/network-scripts/ifcfg-*` files, each one per driver.

* First, installing components:

      sudo yum update
      sudo yum install redhat-lsb-core wget epel-release net-tools nano htop

* Configure the network interfaces:

      sudo nano /etc/sysconfig/network-scripts/ifcfg-eth0

* Add or modify:

      BOOTPROTO=static
      ONBOOT=yes
      IPADDR=192.168.100.129
      NETMASK=255.255.255.0
      NETWORK=192.168.100.0
      GATEWAY=192.168.100.1
      BROADCAST=192.168.100.255
      DNS1=8.8.8.8
      DNS2=8.8.4.4

* Restart the services:

      sudo systemctl restart network
      sudo systemctl start sshd.service

* Now, we connect from the OS host through ssh:

      ssh jenazad@192.168.100.129

