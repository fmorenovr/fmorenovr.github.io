---
layout: post
title:  "Using PCSX2 Game emulator"
date:   2016-05-20 02:35:46 -0500
categories: Games
---
## pcsx2

Is a Play Station 2 emulator.

### Installing

You should have the bios, you can get it by pressing [here](/files/bios.zip).

Then install:

    sudo add-apt-repository ppa:gregory-hainaut/pcsx2.official.ppa
    sudo apt-get update
    sudo apt-get install pcsx2

### Errors

* If you have some dependencies error, you should try this:

      sudo apt-get install wine
      sudo apt-get install canonical-certification-client libcheese-gtk23 libcheese7 libclutter-1.0-0 libclutter-gtk-1.0-0 libcogl15 libclutter-gst-2.0-0 gstreamer1.0-clutter

* If an error is canonical-certification-client, do this:

      sudo apt-get install canonical-certification-client
      sudo apt-get purge unity-control-center gnome-control-center
      sudo apt-get install canonical-certification-client
      sudo apt-get install unity-control-center (get this package back.)

### Executing games on DOSbox

After download bios, uncompress and move to the `~/.config/pcsx2/bios`. Then, download the iso games and run.

Here i show you an example with Megaman X - collection (My favourite game)

![PCSX2 Example](/assets/games/pcsx2_example.jpg)
