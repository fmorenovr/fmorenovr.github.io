---
layout: post
title:  "Installing GNOME-Builder, an IDE to develops projects using remote repositories."
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

* First Method, we check our gnome-shel version `Not Recommended`:

  ![gnome-version][gnomeversion]

      sudo dnf install gnome-builder

  If you have some troubles trying to run Builder, just reboot your system.

* Second Method, install flatpak `Recommended`:

      sudo dnf install -y flatpak flatpak-libs flatpak-builder

* Then, we nee add some dependencies:

      wget https://sdk.gnome.org/keys/gnome-sdk.gpg
      flatpak --user remote-add --gpg-import=gnome-sdk.gpg gnome https://sdk.gnome.org/repo/
      flatpak --user install gnome org.gnome.Sdk 3.24
      flatpak install --user --from https://git.gnome.org/browse/gnome-apps-nightly/plain/gnome-builder.flatpakref?h=stable

* Show the lisst of Flatpak repositories:

      flatpak remote-ls gnome-apps

* Install dependencies for Gnome-Builder:

      flatpak run org.gnome.Builder

  For each of theses commmands, the system will ask you for your password:

  ![flatpak][flatpak_url]

  It takes a few 30 minutes to install dependencies.

  ![flatpak_installing][fpk_install]

* Then, run builder:

  ![Builder][GNOME-builder]

* Then, you can clone any repository using the url of the project you want to clone. You can find a complete list of GNOME project [here][project-list]. I choose [gnome-bluetooth](https://git.gnome.org/browse/gnome-bluetooth/).  

  So, click on clone button, paste the project url and go.

  ![clone][clonebutton]

* Finally, you will have your project cloned into gnome-builder:

  ![builder-init][gnome-builder-init]

* Now, we can try clone any repository, for example I use my own [repo][repo-url].

  ![builder-clone][builderClone]

  Then, you can edit your files:
  
  ![builder-ide][builderIDE]

* Finally, you can see a list of cloned projects.

  ![builder-list][builderList]

[builderList]:        /assets/IDEs/GNOME-Builder/gnome-builder-list.png
[builderIDE]:         /assets/IDEs/GNOME-Builder/gnome-builder-own-repo.png
[builderClone]:       /assets/IDEs/GNOME-Builder/gnome-builder-clone.png
[repo-url]:           https://github.com/Jenazad/developConfig/
[gnome-builder-init]: /assets/IDEs/GNOME-Builder/gnome-builder-init.png
[fpk_install]:        /assets/IDEs/GNOME-Builder/flatpak_installing.png
[vm-url]:             /blog/virtual-machines/2017-03-20/Using-Virt-Manager-Tool
[flatpak_url]:        /assets/IDEs/GNOME-Builder/flatpak_exe.png
[clonebutton]:        /assets/IDEs/GNOME-Builder/gnome-bluetooth.png
[project-list]:       https://git.gnome.org/browse/
[gnomeversion]:       /assets/graphicalShell/GNOME/gnome-version.png
[GNOME-builder]:      /assets/IDEs/GNOME-Builder/gnome-builder.png
