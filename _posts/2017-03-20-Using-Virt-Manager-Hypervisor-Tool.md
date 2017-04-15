---
layout: post
title:  "Using Virt-Manager VM Hypervisor Tool"
date:   2017-03-20 14:58:05 -0500
categories: Virtual-machines
---
# Virt-Manager

Is a desktop-driven virtual machine manager with which users can manage virtual machines (VMs).  
Virt-Manager is a Light virtualizer using KVM and Qemu.

## Installing

* First, we shoul know how many CPUs can support hardware virtualization:

      grep --color -e -svm -e vmx /proc/cpuinfo
      egrep -c '(svm|vmx)' /proc/cpuinfo

* Then, installing virt-manager, qemu and kvm:

      sudo apt-get install qemu-kvm libvirt-bin virtinst kvm virt-manager virt-viewer

* Add our principal user to the libvirtd group:

      sudo adduser jenazad libvirtd

* Create a directory (pool) where you can store the images of each OS (vol):

      mkdir /home/$USER/.virtManager/images

* Initializing the virtual manager:

      sudo virt-manager

* Shows a list of all guest OS:

      sudo virsh -c qemu:///system list --all

## Storage pool

A pool store the information of a group of OS (image).

* Create/Define a pool:

      sudo virsh pool-create-as --name stgname --type dir --target "/home/$USER/.virtManager/images"
      sudo virsh pool-define-as --name stgname --type dir --target "/home/$USER/.virtManager/images"

* Edit a pool:

      sudo virsh pool-edit --pool stgname

* List all pools:

      sudo virsh pool-list --all

* Initializing pool:

      sudo virsh pool-start stgname
      sudo virsh pool-autostart stgname

* Delete/Undefined pool:

  If pool was defined, only write destroy, if not, write all this commands:

        sudo virsh pool-destroy stgname
        sudo virsh pool-delete stgname
        sudo virsh pool-undefine stgname

## Virtual Networks

* Edit the virtual network:

      sudo virsh net-edit netname

* List all virtual networks:

      sudo virsh net-list --all

## Storage Volumen

A vol is the image installed of a OS.

* List all vols in a pool:

      sudo virsh vol-list --pool stgname

* Create vol:

      sudo virsh vol-create-as --pool stgVirt --name volname.qcow2 --capacity 20G --format qcow2

* Delete vol:

      sudo virsh vol-delete --pool stgname volname.qcow2

## Virtual Machines

A virtual machine is a guest OS on another OS (host), you can see the xml configuration files on `/etc/libvirt/qemu/`

* Create a VM:

    * From local iso (example installing Deepin 15.3):

          sudo virt-install \
          --connect qemu:///system \
          --name Deepin15.3_VM \
          --memory 2048 \
          --vcpus 1 \
          --network network=virtualnetworkNAT,model=virtio \
          --os-type linux \
          --os-variant generic \
          --disk path=/home/$USER/VirtStg/images/deepin15.qcow2,size=20 \
          --cdrom /home/$USER/Documents/deepin-15.3-amd64.iso \
          --graphics spice \

      ![deepin_installing](/assets/VM_emulator/virt-manager/installing_deepin.png)

    * From remote `http/ftp` server (example insalling Debian 8.0):
    
          sudo virt-install \
          --connect qemu:///system \
          --name Debian8.7 \
          --memory 2048 \
          --vcpus 1 \
          --network network=virtualnetworkNAT,model=virtio \
          --os-type linux \
          --os-variant generic \
          --disk path=/home/$USER/VirtStg/images/debian8.qcow2,size=20 \
          --location 'http://ftp.nl.debian.org/debian/dists/jessie/main/installer-amd64/' \
          --graphics none \
          --console pty,target_type=serial \
          --extra-args 'console=ttyS0,115200n8 serial'

      ![debian_installing](/assets/VM_emulator/virt-manager/installing_debian.png)

* Delete a VM:

      sudo virsh destroy vmname
      sudo virsh undefine vmname

* List all VM:

      sudo virsh list --all

* Start/reboot/shutdown VM:

      sudo virsh start vmname
      sudo virsh reboot vmname
      sudo virsh shutdown vmname

* Save/restore state of a VM:

      sudo virsh save vmname vmname-20170318.state
      sudo restore vmname-20170318.state

* Connect to VM:

      sudo virt-viewer -c qemu:///system vmname

* Clone a VM:

      sudo virt-clone --connect=qemu:///system -o originalvm -n copyvm -f /path/to/copyvm.qcow2

* Create VM using virt-manager interface:

    * step 1: Choose the method to install.

      ![step-1](/assets/VM_emulator/virt-manager/create_VM_step_1.png)

    * step 2: Select the ISO image.

      ![step-2](/assets/VM_emulator/virt-manager/create_VM_step_2.png)

    * step 3: Set RAM memory.

      ![step-3](/assets/VM_emulator/virt-manager/create_VM_step_3.png)

    * step 4: Create/Set a disk storage for the file system of the guest OS.

      ![step-4](/assets/VM_emulator/virt-manager/create_VM_step_4.png)

    * step 5: Write the OS name, select the network and choose (optional) more configurations.

      ![step-5](/assets/VM_emulator/virt-manager/create_VM_step_5.png)

    * step 6 (optional): Advanced configurations.

      ![step-6](/assets/VM_emulator/virt-manager/create_VM_step_final.png)

### Configure some VM OS

* [Debian 8.7][debian-networking]

* [Ubuntu server 16.04][ubuntu-networking]

* [Deepin 15.3][deepin-networking]

* [CentOS 7.3][centos-networking]

* [Fedora server 25][fedora-networking]


[debian-networking]: /pages/debian_networking
[ubuntu-networking]: /pages/ubuntu_networking
[deepin-networking]: /pages/deepin_networking
[redhat-networking]: /pages/redhat_networking
[centos-networking]: /pages/centos_networking
[fedora-networking]: /pages/fedora_networking
