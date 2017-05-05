---
layout: post
title:  "Setting Up a Firewall using ufw on Linux."
date:   2017-05-04 00:15:12 -0500
categories: System-Settings
---
# UFW

UFW, or Uncomplicated Firewall, is an interface to iptables that is geared towards simplifying the process of configuring a firewall.  
If your distro don't have ufw, install it:

    sudo apt-get install ufw

Then, we have options like:  
* Enable/Disable firewall:

      sudo ufw enable
      sudo ufw disable

* Show status and detailed status:

      sudo ufw status
      sudo ufw status verbose

* Show rules list numbered:

      sudo ufw status numbered

* Blocks/Allows all incoming LAN traffic from internet:

      sudo ufw default deny incoming
      sudo ufw default allow incoming

* Blocks/Allows all outgoing LAN traffic to internet:

      sudo ufw default deny outgoing
      sudo ufw default allow outgoing

* Blocks/Allows connections through the port 45 (like ssh):

      sudo ufw deny 45
      sudo ufw allow 45

* Blocks/Allows connections from a specific ip:

      sudo ufw deny from 52.35.156.45
      sudo ufw allow from 52.35.156.45

* Blocks/Allows connections from a specific ip through a specific port 45:

      sudo ufw deny from 52.35.156.45 to any port 45
      sudo ufw allow from 52.35.156.45 to any port 45

* Blocks/Allows connections from a specific subnet (any using a ip in range 192.35.156.1 - 192.35.156.254):

      sudo ufw deny from 192.35.156.0/24
      sudo ufw allow from 192.35.156.0/24

* Blocks/Allows connections through the port 45 from a specific subnet (any using a ip in range 192.35.156.1 - 192.35.156.254):

      sudo ufw deny from 192.35.156.0/24 to any port 45
      sudo ufw allow from 192.35.156.0/24 to any port 45

* Blocks/Allows connections through the port 53 on TCP/UDP:

      sudo ufw deny 53/udp
      sudo ufw allow 53/udp
      sudo ufw deny 53/tcp
      sudo ufw allow 53/tcp

* Blocks/Allow a port ranges on tcp/udp:

      sudo ufw allow 6000:6007/tcp
      sudo ufw allow 6000:6007/udp

* Blocks/Allows Connections to a Specific Network Interface (e.g. eth0:

      sudo ufw deny in on eth0 to any port 15
      sudo ufw allow in on eth0 to any port 15

* Delete a Rule by number(for example, the 2th rule on the list):

      sudo ufw delete 2

* Delete rule (delete rule http and 2044):

      sudo ufw delete allow http
      sudo ufw delete allow 2044

* Reset (by default) configuration:

      sudo ufw reset

