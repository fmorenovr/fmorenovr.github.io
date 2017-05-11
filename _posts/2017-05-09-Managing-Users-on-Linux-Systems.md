---
layout: post
title:  "Managing users in Linux Systems."
date:   2017-05-09 00:20:12 -0500
categories: System-Settings
---
## Managing users and groups

In all machines, we should create an user to manage the system.  
Best way to create users and groups, `Recommended`:

* Create/Delete new group:

      sudo addgroup jclustergroup
      sudo delgroup jclustergroup

* Add/Delete user to a specific group or system (empty):

      sudo adduser juser [jclustergroup/empty]
      sudo deluser juser [jclustergroup/empty]

* Add/Change password to user:

      sudo passwd juser

We can use lower/upper case in names, `Not recommended`:

* Create/Delete new group:

      sudo groupadd JClusterGroup
      sudo groupdel JClusterGroup

* Create/Delete new user:

      sudo useradd Juser
      sudo userdel Juser

* Create new user with a group named `JClusterGroup` with home `/home/juser` and with CLI `/bin/bash`

      sudo useradd -g JClusterGroup -d /home/Juser -m -s /bin/bash Juser

* Change users permissions:

      sudo chown -R <username> <files>

  ![own][chown]

* Change groups permisions:

      sudo chgrp -R <groupname> <files>

  ![grp][chgrp]

* Change actions permissions:

      sudo chmod ugo-rw+x <filename>

  We add execution permission without read/write permission.

[chgrp]:    /assets/systemCommand/chown-grp-mod/chgrp.png
[chown]:    /assets/systemCommand/chown-grp-mod/chown.png
