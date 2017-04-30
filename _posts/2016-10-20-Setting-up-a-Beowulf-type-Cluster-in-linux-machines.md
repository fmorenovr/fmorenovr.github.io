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
    sudo apt-get install openssh-client

### creating a public-private key

Public key: Encrypt messages - transmitter (store in authorized_keys)
Private key: Decrypt messages - receiver

Then we generate a RSA key pair:

    ssh-keygen -t rsa

or:

    sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key

This, generate files `id_rsa` and `id_rsa.pub` on directory `.ssh`.  
Create `authorized_keys` file:

    cat id_rsa.pub >> authorized_keys

Then, change permissions:

    sudo chmod 700 ~/.ssh
    sudo chmod 600 ~/.ssh/authorized_keys

Finally, we need to configure `/etc/ssh/sshd_config` file.  
First, make a copy and then modify:

    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original

Then, modify and add:

    PermitRootLogin no
    PubkeyAuthentication yes
    PasswordAuthentication no
    Port 254
    # Time to log
    LoginGraceTime 30
    # any Host.
    Allowusers Jremote
    # just 192.168.0.25
    AllowUsers Jremote@192.168.0.25
    # any ip of the network 192.168.0.*
    AllowUsers Jremote@192.168.0.*
    # Jremote can connect from any domain, Jremota just connect from that domain
    AllowUsers Jremote@*.pato.com  Jremota@ventas.pato.com    

Now, we restart the service:

    sudo /etc/init.d/ssh restart

### Copying public keys to remote nodes.

Copying the public key to a remote host (nodes):

    cat ~/.ssh/id_rsa.pub | ssh remotePC@remoteHost 'mkdir -p ~/.ssh ; cat >> ~/.ssh/authorized_keys'

Do the same in Jmaster and Jnodes0X.  
* Then, we can connect without password using:

    ssh remotePC@remoteHost -p 254

* To copy files from remote to local (Download)

    scp -r username@hostname:/path/to/file /path/to/destination

* To copy files from the local to the remote (Upload)

    scp -r /path/to/file username@hostname:/path/to/destination

* By a specific port:

    scp -r -p xxxx username@hostname:/path/to/file /path/to/destination
 
## Enabling Firewall

First, we need to check the applications that require conections:

    sudo ufw app list
    sudo ufw disable

Then, allows OpenSSH:

    sudo ufw allow OpenSSH
    sudo ufw enable
    sudo ufw status


