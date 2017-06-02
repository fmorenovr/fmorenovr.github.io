---
layout: post
title:  "GNOME Boxes, a fast View."
date:   2017-05-31 00:20:12 -0500
categories: GUI_app
---
# GNOME Boxes

For this guide, I use my Fedora Workstation 25 Virtual Machine installed on my localhost using virt-manager, you can see how download and install pressing [here][vm-url].

GNOME Logs is a log viewer for the systemd journal

    sudo dnf install gnome-boxes

Boxes use Qemu to virtualize/emulate machines and it is integrate with KVM. Also uses libvirt, by default uses spice to connect to remote VM, Boxes accept VNC too.

Once installed, you hace this:

![boxes-init][boxes_init]

## Creating new VM.

Now, we create a new VM

![boxes-new][boxes_new]
  
We choose URL (maybe you can choose ISO).

![boxes-new-url][boxes_new_url]

Then, you must wait for installation.

![boxes-install][boxes_install]

## Aplications

* See a window with your Virtual Machines.
* Can Manage your VM as virt manager


[vm-url]:         /blog/virtual-machines/2017/03/20/Using-Virt-Manager-Tool
[boxes_init]:     /assets/GUIApp/Boxes/boxes_init.png
[boxes_new]:      /assets/GUIApp/Boxes/boxes_new.png
[boxes_new_url]:  /assets/GUIApp/Boxes/boxes_url_new.png
[boxes_install]:  /assets/GUIApp/Boxes/boxes_installing.png

