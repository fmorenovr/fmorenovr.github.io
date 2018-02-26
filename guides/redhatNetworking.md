---
layout: page
title: "RedHat base OS network configuration"
subtitle: "RedHat base OS network configuration"
description: "Configure /etc/sysconfig/network-scripts/ifcfg-* files"
permalink: /guides/redhat_networking
---

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

