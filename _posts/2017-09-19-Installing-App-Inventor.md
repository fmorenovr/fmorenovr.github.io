---
layout: post
title:  "Installing App Inventor and developing games."
date:   2017-09-19 00:25:12 -0500
categories: Tools
---
# App Inventor

App Inventor is an application of MIT to teach in a easy way how to program mobile apps. Through a methodology based on games like scratch.

How to install:

* First, install 32-bits architecture libraries.

      sudo apt-get install lib32z1
      sudo apt-get install lib32stdc++6

* Second, Download the debian package installer pressing [here](http://appinv.us/aisetup_linux_deb).

* Third, once downloaded, install using dpkg command:

      sudo dpkg --install appinventor2-setup_2.3_all.deb

  The software will be installed under `/usr/google/appinventor`.

* Fourth, go to [appInventor-WebPage](http://ai2.appinventor.mit.edu/) (You should use gmail account).

  ![aiStarterWeb][aiStarterWebi]

* Fifth, Create a new project, i called *FlappyBird*:

  ![aiNewProject][newProject]

* Sixth, You'll have this screen that you can start to develop your app:

  ![aiproject][project]

* Seventh, Download APK for your mobile phone pressing [here](http://appinv.us/companion).

* Eighth, Now you can work using different ways:

    - Connect via USB:
        To do this whay, you should start your service on your computer.  
        Set up the service running the script `aiStarter` in `/usr/google/appinventor/commands-for-Appinventor`.

        ![aiStarter][aiStarterprocess]
        
        Then, press on Connect->USB and wait connection . . .
        ![aiUSB][USB]
    
    
    - Connect via Wi-Fi:  
        To do this way, you should press on **_Build -> APP_** (could be QR or download apk).  
        I choose QR:
        
        ![aiQR][QR]
        
        Then, In your mobile phone (with mit app installed) choose on **_Scan QR Code_**.  
        Once scanned, an url appears. Press on **_connect with code_**.  
        You app will be installed on your phone.
        
        ![app-1][app1] ![app-2][app2]

    - Emulator:
        To do this way, you should press on **_Connect -> Emulator_**.
        
        ![aiEmulator][emulator]

# Example

* Then, I show you an example. First create a project on `Projects -> start new project `, choose a name and press `ok`.

* Using the interface web, just drag items (buttons, sensors, media, etc) in the Designer tab.
  ![ai2designer][ai2-designer]

* Then, you should make the logic in the Blocks tab.
  ![ai2Blocks][ai2-blocks]
    
* Finally, generate apk using QR method and try in your mobile phone and have fun :D  
  Or Generate apk and install on your mobile phone, or just run the emulator.


[aiStarterprocess]:   /assets/tools/appInventor/aiStarter.png
[aiStarterWebi]:      /assets/tools/appInventor/appInventor-web.png
[newProject]:         /assets/tools/appInventor/appInventor-newproject.png
[project]:            /assets/tools/appInventor/appInventor-projectblank.png
[QR]:                 /assets/tools/appInventor/appInventor-build.png
[USB]:                /assets/tools/appInventor/appInventor-USB.png
[app1]:               /assets/tools/appInventor/appInventor-app1.png
[app2]:               /assets/tools/appInventor/appInventor-app2.png
[emulator]:           /assets/tools/appInventor/appInventor-emulator.png
[ai2-designer]:       /assets/tools/appInventor/appInventor-example_designer.png
[ai2-blocks]:         /assets/tools/appInventor/appInventor-example_blocks.png

