---
layout: post
title:  "Using DOS for emulate games"
date:   2016-08-13 02:35:46 -0500

tags:
  - DOSBOX
  - ZNES
  - Game Emulator
  - Megaman
  - Ubuntu

categories:
  - Games
---

Here you'll learn to download and setup DOS console.

## DOSBOX

Dosbox is a shell-terminal that allows execute programs designed to run in DOS.

### Installing

Note: DOSBox only recognized files, directories inside the path `/home/$USER/` whose names only have 8 letters.

    sudo apt-get install dosbox
    dosbox

### Executing games on DOSBOX

1. Run `dosbox` for first time, `.dosbox/dosbox-0.74.conf` will be created.

   ![DOSBOX_first][dosbox_first]

2. In `/home/$USER/.dosbox` creates the directory `Games`, here we put the directories with the programs executable for DOS.  
   Then, modify the file `.dosbox/dosbox-0.74.conf`:

        [autoexec]
        # mounts C disk the path of ~/.dosbox/Games
        mount c ~/.dosbox/Games

        # mounts D disk like CDROM
        # mount d /media/cdrom -t cdrom

        # mounts image on the D disk
        # imgmount D /home/$USER/imagenes/game.iso -t iso

        # ES keyboard
        keyboardlayout=sp

### Example

In `/home/$USER/.dosbox/Games`, copies the game directory and rename to a short name (<=8 letters).

* We use Megaman, just download the [Iso game][iso_mmx] or press [here][zip_mmx].  
* Uncompress on the directory `.dosbox/Games` and rename the game directory (from `mega-man-x` to `MMX`).  
* Launch dosbox, if we configure the `dosbox-0.74.conf` file, just write `C:` and dosbox show the content of `.dosbox/Games` content.

Here is the elements in MMX directory:  
![MMX_tree][mmx_tree]

Then, do this:

    Z:\>
    Z:\>C:
    C:\>cd MMX
    C:\MMX>

Here, we run `tdujam.exe` on DOSBOX, so write:

    C:\MMX>tdujam

![tdujam_Install][tdujam_install]

Select `Install Game`, on the option "  Install to what drive" write "C":

![tdujam_Installing][tdujam_installing]

Once installed, we run the game:

    C:\MMX>MMXRUN

Here I show you an example with Megaman X (one of my favourite games)

![DOS_Example][DOSBOX_img]

[zip_mmx]:            /files/mega-man-x.zip
[iso_mmx]:            http://www.myabandonware.com/game/mega-man-x-2wh
[DOSBOX_first]:       /assets/games/DOS/dosbox_first.png
[MMX_tree]:           /assets/games/DOS/mmx_dir.png
[tdujam_install]:     /assets/games/DOS/mmx_tdujam.png
[tdujam_installing]:  /assets/games/DOS/mmx_installing.png
[DOSBOX_img]:         /assets/games/DOS/dosbox_example.png
