---
layout: page
subtitle: "CentOS minimal 7.3 networking"
description: "configure /etc/sysconfig/network-scripts/ifcfg-* file"
permalink: /docs/redhat_networking
---
### Red Hat Enterprise Linux based OS

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

* Now, we connect from the OS host through ssh:

      ssh jenazad@192.168.100.129


