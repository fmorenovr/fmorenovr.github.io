---
layout: post
title:  "Using Qemu VM emulator"
date:   2016-12-18 19:40:16 -0500
categories: Virtual-machines
---
### Qemu

For more information about arguments see the documentation [Qemu doc](https://wiki.gentoo.org/wiki/QEMU/Options)

Is an emulator of an OS inside another OS without partition the hard disk, instead that qemu uses the path of directories of the images in the OS host.

#### Instaling virtual machines

* Create a directory for the qemu images:

      mkdir ~/.qemu/qemuVM

* Create a directory for each OS, where:

  * Create a directory:

        mkdir OSname

  * Create a VHD (virtual hard disk) for the VM:

        qemu-img create -f qcow2 qemu_disk.qcow2 20G

    Or the format qcow2:

        qemu-img create ubuntu.img 20G

    qcow: QEMU copy-on-Write, specifies the type of image disk, where 20G is the memory amount to be used.

  * Create a distro of the iso image and then install:

        qemu-system-x86_64 -drive file=qemu_disk.img,if=virtio,index=0 -cdrom OS-server.iso -m 640 -boot d -net nic,macaddr=52:54:00:fa:ce:05,model=virtio -net user,hostfwd=tcp::2005-:22

    or also:

        qemu-system-x86_64 -hda ubuntu.img -boot d -cdrom /home/$USER/path/to/iso/OS-server.iso -m 640

    After the installation, run:

        qemu-system-x86_64 -drive file=qemu_disk.img,if=virtio,index=0 -net nic,macaddr=52:54:00:fa:ce:05,model=virtio  -net user,hostfwd=tcp::2005-:22

    or also:

        qemu-system-x86_64 -hda ubuntu.img -m 640

Here i show you an example with Ubuntu 15.04 (yeah, i did this 2 years ago).

![Qemu Exmaple](/assets/VM_emulator/qemu_example.jpg)
