---
layout: post
title:  "Installing GNOME Pomodoro, a time managment tool."
date:   2017-05-16 00:20:12 -0500

tags:
  - GNOME
  - Ubuntu
  - Timer
  - Pomodoro
  - GNOME
  - Fedora
  
categories:
  - GUI_app
---

Here you'll learn how to download and setup Pomodoro time manager tool in your computer to organize your works.

# GNOME Pomodoro

For this guide, I use my Fedora Workstation 25 Virtual Machine installed on my localhost using virt-manager, you can see how download and install pressing [here][vm-url].

* This application is a time management tool, that uses the pomodoro technique. it intends to improve productivity and concentration by taking programmed breaks.  
Then, install:

      sudo dnf install gnome-shell-extension-pomodoro

## Technique

Pomodoro technique have six steps:

* Decide on the task to be done.
* Set the pomodoro timer (usually is 25 minutes).
* Work on the task until the timer rings.
* After the rings, put a checkmark on a piece of paper (todo list e.g.).
* If you have fewer than four checkmarks, take a short break (3–5 minutes), then go to step 2.
* After four pomodoros, take a longer break (15–30 minutes), reset your checkmark count to zero, then go to step 1.

it can be used like `TODO` list.

## Testing

Once installed, you'll have this window:

![pom_init][pomodoro-init]

If you press play, pomodoro starts by default with 25 minutes on timer.  
Then you can access to modify preferences or breaks time, sounds, notifications pressing on pomodoro menu.

![pom_menu][pomodoro-menu]

And you'll see this configuration window:

![pom_preferences][pomodoro-preferences]

Once the chronometer finished, shows a new timer:

![pom_break][pomodoro-break]

[vm-url]:               /virtual-machines/Using-Virt-Manager-Tool
[pomodoro-init]:        /assets/GUIApp/Pomodoro/pomodoro_init.png
[pomodoro-menu]:        /assets/GUIApp/Pomodoro/pomodoro_menu.png
[pomodoro-preferences]: /assets/GUIApp/Pomodoro/pomodoro_preferences.png
[pomodoro-break]:       /assets/GUIApp/Pomodoro/pomodoro_break.png
