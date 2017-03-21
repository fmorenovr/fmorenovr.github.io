---
---
### Fedora Server 25 VM

* First, installing components:

    sudo yum update
    sudo yum install redhat-lsb-core htop

* Configure the network interfaces:

    sudo nano /etc/sysconfig/network-scripts/ifcfg-ens3

* Add or modify:

    BOOTPROTO=static
    ONBOOT=yes
    IPADDR=192.168.100.131
    NETMASK=255.255.255.0
    NETWORK=192.168.100.0
    GATEWAY=192.168.100.1
    BROADCAST=192.168.100.255
    DNS1=8.8.8.8
    DNS2=8.8.4.4

* Restart the services:

    sudo systemctl restart network

* Now, we connect from the OS host through ssh:

    ssh jenazad@192.168.100.131


