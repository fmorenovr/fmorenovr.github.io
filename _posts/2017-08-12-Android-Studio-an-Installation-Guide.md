---
layout: post
title:  "Android Studio, An installation guide."
date:   2017-08-12 00:20:12 -0500
categories: IDEs
---
## Android Studio

Android Studio is an IDE to develop android OS applications.

### Requeriments

* Java: Try with java-8

      sudo add-apt-repository ppa:webupd8team/java
      sudo apt-get update
      sudo apt-get install oracle-java8-installer
      sudo apt-get install oracle-java8-set-default

* Android Studio: you can download the zip file, uncompress and run the script `studio.sh`:

      wget https://dl.google.com/dl/android/studio/ide-zips/2.1.2.0/android-studio-ide-143.2915827-linux.zip
      unzip android-studio-ide-143.2915827-linux.zip
      cd android-studio/bin
      ./studio.sh

![astudio](/assets/IDEs/AndroidStudio/android-studio.png)

## Android Shell

Is a method that you can connect with your smartphone using SSH connection (through a bash shell).

* First, list a usb devices:

      lsusb
      
  ![lsusb](/assets/systemCommand/adb/lsusb.png)

    Here, you can see my motorola device with Id `22b8`.
    
* Second, install android-tools:

      sudo apt-get install android-tools-adb

* Third, Creates a file in `/etc/udev/rules.d/` with name `51-android.rules`:

      sudo touch etc/udev/rules.d/51-android.rules 
      sudo nano etc/udev/rules.d/51-android.rules 
      
  And add:
  
      SUBSYSTEM=="usb", SYSFS{idVendor}=="22b8", OWNER="jenazad" GROUP="jenazad" 

  Where `idVendor` is the id of my device, `OWNER` and `GROUP` is the user permissions.
  
* Fourth, restart udev service:

      sudo services udev restart

* Fifth, check for devices:

      adb devices

  ![devices](/assets/systemCommand/adb/devices.png)

* Sixth, connect with your mobile:

      adb shell
      
  During the process, your mobile will receive a notification to connect through ssh like:
  
  ![notify](/assets/systemCommand/adb/mobile-shell.png)
  
  Accept, and now you can manage your data through shell.

