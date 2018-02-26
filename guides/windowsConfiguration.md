---
layout: page
title: Windows Light-Environment configuration
subtitle: "Windows Light-Environment configuration"
description: "Download and install programs for a Light-Environment Windows."
permalink: /guides/light_environment_windows
---
Configuration to have a lightweight system.

## Shutdown System

Command to shutdown Windows OS using cmd:

    shutdown /s /t 0

### Create exe file

* Right Click -> new -> direct acess:  
* Options:  
    * Suspend:  
        `C:\Windows\System32\Rundll32.exe powrprof.dll`
    * Hibernate:  
        `C:\Windows\System32\shutdown.exe /h`
    * Shutdown:  
        `C:\Windows\System32\shutdown.exe -s -t 00`
    * shutdown:  
        `C:\Windows\System32\shutdown.exe /s /t 0`
    * Reboot:  
        `C:\Windows\System32\shutdown.exe -r -t 00`



