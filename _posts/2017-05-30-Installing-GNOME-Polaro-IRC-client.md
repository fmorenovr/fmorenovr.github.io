---
layout: post
title:  "Installing GNOME Polari, a IRC Client."
date:   2017-05-30 00:20:12 -0500
categories: GUI_app
---
# GNOME Polari

For this guide, I use my Fedora Workstation 25 Virtual Machine installed on my localhost using virt-manager, you can see how download and install pressing [here][vm-url].

* This application is a minimal IRC client. It is designed to distill the IRC experience down to a super-simple interface. It also uses the GNOME telepathy backend, and allows you to reply to chat messages straight from the notifications.  
Then, install:

      sudo dnf install polari

Polari is an exclusive IRC Client that is the big difference with [empathy][empathy-url].

## Testing

Once installed, you'll have this window:  
You can see your chats (previously we use Empathy, so appears a list of created chats).  

![pol_init][polari-init]

If you press plus button, you can add net and choose your chat room.  

![pol_new][polari-new-chat]

You can see your chats (previously we use Empathy, so appears a list of created chats). Then, you can choose your chat and connect.  

![pol-chats][polari-chats]

## Functionalities

* IRC Client chat
* Search for Id user and autocomplete to talk
* Send Images and text messages.


[vm-url]:            /blog/virtual-machines/2017/03/20/Using-Virt-Manager-Tool
[empathy-url]:       /blog/gui_app/2017/05/06/Installing-Empathy-a-IM-client
[polari-init]:       /assets/GUIApp/Polari/polari_init.png
[polari-chats]:      /assets/GUIApp/Polari/polari_chats.png
[polari-new-chat]:   /assets/GUIApp/Polari/polari_new_chat.png
[polari-error]:      /assets/GUIApp/Polari/polari_error_connection.png
