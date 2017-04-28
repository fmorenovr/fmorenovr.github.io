---
layout: post
title:  "Using PCSX2, a PlayStation 2 Games Emulator"
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

### Executing games on PCSX2

After download bios, uncompress and move to the `~/.config/pcsx2/bios`.  
Then, execute PCSX2 for first time.

The first window, you can select your language (I choose spanish) and press next.

![PCSX2_first][pcsx2_fisrt]

Then, PCSX2 shows a configuration window, press next or "siguiente".

![PCSX2_config][pcsx2_config]

Next, select your bios files, I always choose `USA 10/02/2006` and press finish or "terminar".

![PCSX2_bios][pcsx2_bios]

Once you finish, pcsx2 shows this.

![PCSX2_init][pcsx2_init]

### Example

You can download Megaman X Collection from [emuparadise][emuparadise_web].  
Once you downloaded the ISO game, start PCSX2, press `CDVD -> select ISO -> Search ...`  
And then, press on `System -> execute CDVD`  
Here i show you an example with Megaman X - collection (My favourite game)

![PCSX2 Example][pcsx2_img]

[emuparadise_web]: https://www.emuparadise.me/Sony_Playstation_2_ISOs/Mega_Man_X_Collection_(USA)/150674
[pcsx2_img]:       /assets/games/PCSX2/pcsx2_example.jpg
[pcsx2_fisrt]:     /assets/games/PCSX2/first_window.png
[pcsx2_config]:    /assets/games/PCSX2/config_pcxs2.png
[pcsx2_bios]:      /assets/games/PCSX2/select_bios.png
[pcsx2_init]:      /assets/games/PCSX2/once_init.png
