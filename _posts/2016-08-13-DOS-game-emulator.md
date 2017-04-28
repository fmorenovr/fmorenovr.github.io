---
layout: post
title:  "Using DOS for emulate games"
date:   2016-08-13 02:35:46 -0500
categories: Games
---
## DOSBOX

Dosbox is a shell-terminal that allows execute programs designed to run in DOS.

### Installing

Note: DOSBox only recognized files, directories inside the path `/home/$USER/` whose names only have 8 letters.

    sudo apt-get install dosbox
    dosbox

### Executing games on DOSbox

1. In `/home/$USER/` creates the directory `.dosbox/Games`

   Here we put the directories with the programs executable for DOS.

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

2. In this directory, puts the game and rename the exe program with a short name (<=8 letters).

    Example:

    * We use Megaman, just download the Iso game.

    * Uncompress on the directory `.dosbox/Games` and rename the game directory (for example MMX).

    * Launch dosbox, if we configure the `dosbox-0.74.conf` file, just write `C:` and dosbox show the content of `.dosbox/Games` content.

    Then, do this:

        Z:\>
        Z:\>C:
        C:\>cd MMX
        C:\MMX>

    Then, if we dont has exe program, we should install the game, so write instead MMXRUN.exe:

        C:\MMX>
        C:\MMX>{install_file_name_exe}
        C:\MMX>{run_file_name_exe}

Here i show you an example with Megaman X (one of my favourite games)

![DOS Example](/assets/games/dos_example.png)
