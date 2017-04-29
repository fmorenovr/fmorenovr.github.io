---
layout: post
title:  "Setting Up a Beowulf Type Cluster in Linux Machines."
date:   2016-10-20 12:15:12 -0500
categories: Cluster_Computing
---
# Cluster

A cluster is a group of servers and other resources that act like a single system and enable high availability and, in some cases, load balancing and parallel processing.

# Setting up a Beowulf type Cluster

Our cluster is named JCluster.

This guide describes how to build a simple cluster in Ubuntu using MPICH.  
We have 5 nodes running ubuntu server with hostnames: Jmaster, Jnode01, Jnode02, Jnode03 and Jnode04.

## Configure our static IP

So first, we configure our IP, DNS on file `/etc/network/interfaces`.  
We need a static IP for a local network in all of them (nodes and master).

    #Ethernet for Jmaster
    auto eth0
    iface eth0 inet static
    address 192.168.125.100
    network 192.168.125.0
    gateway 192.168.125.1
    netmask 255.255.255.0
    broadcast 192.168.125.255
    dns-nameservers 8.8.8.8 8.8.4.4

## Configure our hosts

Then, in all computers (nodes and master) edit the file `/etc/hosts` like this way:

* On master:

      127.0.0.1        localhost
      127.0.1.1        Jmaster
      192.168.125.101  Jnode01
      192.168.125.102  Jnode02
      192.168.125.103  Jnode03
      192.168.125.104  Jnode04

* On node03 for example:

      127.0.0.1        localhost
      127.0.1.1        Jnode03
      192.168.125.100  Jmaster
      192.168.125.101  Jnode01
      192.168.125.102  Jnode02
      192.168.125.104  Jnode04

## Configure our hostname

If you want, you can change your hostname on file `/etc/hostname` and then reboot your system.

## Install NFS

The Network File System (NFS) is a client/server application that allows us to create a folder on the master node and have it synced on all the other nodes. This folder can be used to store programs.

* Install on master:

      sudo apt-get install nfs-kernel-server

* Install on node:

      sudo apt-get install nfs-common

### Sharing Master folder

Make a folder in all nodes and master, our data and programs will be store in this folder.  
So, we make a folder and change credentials for nobody.

    sudo mkdir /forShare
    sudo chown nobody:nogroup /forShare/

So, on file `/etc/exports` write:

    # share forShare folder to any
    /forShare  *(rw,sync,no_subtree_check)
    # share home folder to hostname1
    /home      hostname1(ro,sync,no_root_squash,no_subtree_check)
    # share /usr/local for all the machines with IP addresses between 192.168.0.0 and 192.168.0.255
    /usr/local 192.168.0.0/255.255.255.0(ro)

* rw = read/write  
* ro = read only

Now restart the nfs service:

    sudo service nfs-kernel-server restart
    sudo systemctl restart nfs-kernel-server

### Mounting Master folder in nodes

In clients, create:

    sudo mkdir /nfs/forShare
    sudo mkdir /nfs/home

Then, we mount folders:

    sudo mount Jmaster:/forShare  /nfs/forShare
    sudo mount Jmaster:/home      /nfs/home

### Mounting Master folder at boot

We can mount the remote NFS shares automatically at boot by adding them to `/etc/fstab` file on the client:

    Jmaster:/forShare  /nfs/forShare       nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0

    Jmaster:/home      /nfs/home           nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0


### Unmounting folder

From clients write:

    sudo umount /forShare
    sudo umount /forShare/home

## Creating a user whose manage shared folder

* Create group:

      sudo groupadd JClusterGroup

* Add user to group:

      sudo adduser Juser JClusterGroup
    
* Delete user to group:

      sudo deluser Juser JClusterGroup

* Delete group:

      sudo groupdel JClusterGroup

* Create user with a group named `JClusterGroup` with home `/home/Juser` and with CLI `/bin/bash`

      sudo useradd -g JClusterGroup -d /home/Juser -m -s /bin/bash Juser

* Add password to user:

      sudo passwd Juser

* Delete user:

      sudo userdel -r Juser

* Finally we change the credentials to Juser:

      sudo chown Juser:JClusterGroup /forShare

## Install OpenSSH

Is a free suite of tools that help secure your network connections (similar to the SSH connectivity tools).

    sudo apt-get install openssh-server

### creating a public-private key

Then we generate a RSA key pair:

    sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key

Then, we need to configure `/etc/ssh/sshd_config` file.  
First, make a copy and then modify:

    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original

Then, modify and add:

    
    PermitRootLogin no
    PubkeyAuthentication yes

Now, we restart the service:

    sudo /etc/init.d/ssh restart


    
    
    
    
    
