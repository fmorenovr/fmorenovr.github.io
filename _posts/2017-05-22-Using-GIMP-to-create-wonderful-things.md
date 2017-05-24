---
layout: post
title:  "Using GIMP to create wonderful things."
date:   2017-05-22 00:20:12 -0500
categories: GUI_app
---
# GIMP

GIMP (GNU Image Manipulation Program) is a software to edit digital images with form bitmaps.

GIMP by default is installed in linux systems, but you can install:

    sudo apt-get install gimp

![gimpInit][gimp-init]

### Shortcuts

GIMP provide a list of shortcuts to manages the GUI making editing images easy and simple:

* Help Menu
    * `F1` Help
    * `Shift+F1` Context Help

      ![gimpHelp][gimp-help]

* Files
    * `Ctrl+N` New image
    * `Ctrl+O` Open image
    * `Ctrl+Alt+O` Open image as new layer
    * `Ctrl+D` Duplicate image
    * `Ctrl+X` Open recent image X
    * `Ctrl+S` Save image
    * `Shift+Ctrl+S` Save under a new name
    * `Ctrl+Q` Quit

* Toolbox
    * `R` Rect Select
    * `E` Ellipse Select
    * `F` Free Select
    * `U` Fuzzy Select
    * `Shift+O` Select By Color
    * `I` Scissors	I
    * `B` Paths
    * `O` Color Picker
    * `M` Move
    * `Shift+C` Crop and Resize
    * `Shift+R` Rotate
    * `Shift+T` Scale
    * `Shift+S` Shear
    * `Shift+P` Perspective
    * `Shift+F` Flip
    * `T` Text
    * `Shift+B` Bucket Fill
    * `L` Blend
    * `N` Pencil
    * `P` Paintbrush
    * `Shift+E` Eraser
    * `A` Airbrush
    * `K` Ink
    * `C` Clone
    * `V` Convolve
    * `S` Smudge
    * `Shift+D` Dodge/Burn
    * `X` Swap Colors
    * `D` Default Colors

      ![gimpLayers][gimp-layers]

### Using GIMP

This is my original image:

![hamster][Hamster]

Then, pressing `f`, we can set points to cut image:

![hamsterCut][HamsterCut]

Next, create a new window, we choose `transparency`:

![gimpnew][gimpNew]

Then, cut and paste in the new window:

![gimpcutnew][gimpCutNew]

With `Ctrl+B` we can show the right menu and `Ctrl+Shift+B` left menu

![hamsterB][hamsterb]


[gimp-init]:      /assets/GUIApp/GIMP/gimp_init.png
[gimp-help]:      /assets/GUIApp/GIMP/gimp_help.png
[gimp-layers]:    /assets/GUIApp/GIMP/gimp_layers.png
[Hamster]:        /assets/GUIApp/GIMP/hamster.png
[HamsterCut]:     /assets/GUIApp/GIMP/hamsterCut.png
[gimpNew]:        /assets/GUIApp/GIMP/gimp_newWindow.png
[gimpCutNew]:     /assets/GUIApp/GIMP/gimp_cut_new.png
[hamsterb]:       /assets/GUIApp/GIMP/hamster_B.png
