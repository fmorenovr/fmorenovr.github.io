---
layout: post
title:  "Installing i3, a Tiling Window Manager for light Environments."
subtitle: Here I'll show you a light desktop environment to save the RAM consume.
date:   2017-05-06 04:05:12 -0500
categories: Window_Manager
---
# i3 window manager

A Tiling Window Manager is a window manager with an organization of the screen into mutually non-overlapping frames.  
i3 don't use a GUI.  
* Installing on Debian based OS:

      sudo -i
      apt-get update
      apt-get install i3

* Configure bar attributes in :

      cat /etc/i3status.conf

* Configurate i3 key-actions in `/etc/i3/config`:

      cat /etc/i3/config

* To lock screen, we add this line in `/etc/i3/config` file:

      bindsym $MOD+SHIFT+x exec i3lock -c 000000 -i ~/.i3/images/file.png

  Where `file.png` is the background image.

You can download my configuration pack pressing [here][i3-url]. Uncompress and copy files.  
For images, create a `~/.i3/images` directory and copy the files there.

## Preview

You can visit this [page][lightEnviron] to compliment a light Environment with i3 WM.  	
Here is an example on my localhost, i3 using Vim, slurm, htop, ranger and alsamixer:

![i3WM][i3-wm]

## Commands shortcuts:

      $mod + Enter        Open terminal
      $mod + A            Focus to "parent"
      $mod + S            Set Stacked (Cascada)
      $mod + W            Set Tabbed
      $mod + E            Set default
      $mod + SpaceBar     Change focus tiling/floating
      $mod + D            dmenu
      $mod + H            Split Horizontal
      $mod + V            Split Vertical
      $mod + J            Foco izquierda
      $mod + K            Focus down
      $mod + L            Focus up
      $mod + ñ            Focus right
      $mod + Shift + Q    Close window
      $mod + Shift + E    Exit to i3
      $mod + Shift + C    Recarcar configuración sin reiniciar
      $mod + Shift + R    Restart i3bar
      $mod + Shift + J    Move window to left
      $mod + Shift + :    Move window to right
      $mod + Shift + K    Move window to down
      $mod + Shift + L    Move window to up
      $mod + Shift + SpaceBar   Change focus tiling/floating
      $mod + Shift + x    Lock Screen


[lightEnviron]:  /guides/light_environment_debian
[i3-wm]:         /assets/WindowManager/Tiling/i3_wm.png
[i3-url]:        https://github.com/Jenazads/i3-wm_personalConfig
