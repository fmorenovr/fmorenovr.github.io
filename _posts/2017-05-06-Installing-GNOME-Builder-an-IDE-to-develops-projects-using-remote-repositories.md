---
layout: post
title:  "Installing GNOME-Builder, an IDE to develops projects using remote repositories."
subtitle: Here you'll learn how to download and use the new IDE GNOME-Builder to clone, modify and solve bugs for the GNOME community.
date:   2017-05-06 00:15:12 -0500
categories: IDEs
---
# GNOME Builder

For this guide, I use my Fedora Workstation 25 Virtual Machine installed on my localhost using virt-manager, you can see how download and install pressing [here][vm-url].

* GNOME-builder is a integrated IDE for GNOME desktop environment and has support of:
  * Version control systems Git.  
  * Developing flatpak applications.  
  > Flatpak allows the same app to be installed on different Linux distributions
  * Is available for C, C++, Vala, Python, etc. programming languages.

* First, we check our gnome-shel version and then install `gnome-builder`:

  ![gnome-version][gnomeversion]

      sudo dnf install gnome-builder

  If you have some troubles trying to run Builder, just reboot your system.

* Next, install flatpak `Recommended`:

      sudo dnf install -y flatpak flatpak-libs flatpak-builder

* Then, we nee add some dependencies:

      wget https://sdk.gnome.org/keys/gnome-sdk.gpg
      sudo flatpak --user remote-add --gpg-import=gnome-sdk.gpg gnome https://sdk.gnome.org/repo/
      sudo flatpak --user install gnome org.gnome.Sdk 3.24
      sudo flatpak install --user --from https://git.gnome.org/browse/gnome-apps-nightly/plain/gnome-builder.flatpakref?h=stable

  For each of theses commmands, the system will ask you for your password:

  ![flatpak][flatpak_url]

* Show the list of Flatpak repositories:

      flatpak remote-ls gnome-apps

* Install dependencies for Gnome-Builder:

      sudo flatpak run org.gnome.Builder

  It takes a few 30 minutes to install dependencies.

  ![flatpak_installing][fpk_install]

* Then, run builder:

  ![Builder][GNOME-builder]

* Then, you can clone any repository using the url of the project you want to clone. You can find a complete list of GNOME project [here][project-list]. I choose [polari](https://git.gnome.org/browse/polari/).  

  So, click on clone button, paste the project url and go.

  ![clone][clonebutton]

* Then, you will have your project cloned into gnome-builder:

  ![builder-init][gnome-builder-init]

* Finally, you can run the application (in this case is Polari IRC):

  ![builder-run][gnome-builder-run]

## Other functionalities

* You can clone any repository, for example I use my own [repo][repo-url].

  ![builder-clone][builderClone]

  Then, you can edit your files and make pull/push on the project:
  
  ![builder-ide][builderIDE]

## Listing cloned projects

* Each time that you start gnome builder, you can see the list of cloned projects.

  ![builder-list][builderList]

[builderList]:        /assets/IDEs/GNOME-Builder/gnome-builder-list.png
[builderIDE]:         /assets/IDEs/GNOME-Builder/gnome-builder-own-repo.png
[builderClone]:       /assets/IDEs/GNOME-Builder/gnome-builder-clone.png
[repo-url]:           https://github.com/Jenazad/developConfig/
[gnome-builder-init]: /assets/IDEs/GNOME-Builder/gnome-builder-init.png
[gnome-builder-run]:  /assets/IDEs/GNOME-Builder/gnome-builder-run.png
[fpk_install]:        /assets/IDEs/GNOME-Builder/flatpak_installing.png
[vm-url]:             /virtual-machines/Using-Virt-Manager-Tool
[flatpak_url]:        /assets/IDEs/GNOME-Builder/flatpak_exe.png
[clonebutton]:        /assets/IDEs/GNOME-Builder/gnome-builder-polari.png
[project-list]:       https://git.gnome.org/browse/
[gnomeversion]:       /assets/graphicalShell/GNOME/gnome-version.png
[GNOME-builder]:      /assets/IDEs/GNOME-Builder/gnome-builder.png
