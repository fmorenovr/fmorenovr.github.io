---
layout: post
title:  "Installing Empathy, a IM and VoIP Client."
subtitle: Here you'll learn how to download and connect through different clients to send messages.
date:   2017-05-06 00:20:12 -0500
categories: GUI_app
---
# Empathy

For this guide, I use my Fedora Workstation 25 Virtual Machine installed on my localhost using virt-manager, you can see how download and install pressing [here][vm-url].

* Empathy Is an Instant Messaging (IM) and voice over IP (VoIP) client which supports text, voice, video, file transfers, and inter-application communication over various IM protocols.

      sudo dnf install empathy

* Once installed, run on shell:

      empathy

  ![Empathy-init][empathy-init]

* Here, enter your details and then choose your username:

  ![Empathy-connect][empathy-connect]

* Then, look for a chatroom, press on the top menu `empathy`:

  ![Empathy-menu][empathy-menu]

* Choose `salas` -> `unirse a una sala`:

  ![Empathy-room][empathy-room]

* Finally, start to talk with other people:

  ![empathy-chat][empathy-chat]

## NOTE

Do not use facebook connection, because `Empathy` uses a deprecated API, this is the reason that `empathy` doesn't connect to facebook.

## Applications

* You could use this chat to communicate with any person without authents in some social network. 
* Or make a LAN chat.

[empathy-chat]:       /assets/GUIApp/Empathy/empathy_chat.png
[empathy-room]:       /assets/GUIApp/Empathy/empathy_room.png
[empathy-menu]:       /assets/GUIApp/Empathy/empathy_menu.png
[empathy-connect]:    /assets/GUIApp/Empathy/empathy_connect.png
[empathy-init]:       /assets/GUIApp/Empathy/empathy_init.png
[vm-url]:             /virtual-machines/Using-Virt-Manager-Tool
