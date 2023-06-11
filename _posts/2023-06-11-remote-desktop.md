---
layout: post
title: "Connecting to Ubuntu via remote desktop"
---

## Introduction
Sometimes its necessary to access remote systems with a desktop/UI interface.

To do this:
 
```
sudo apt install xrdp
sudo systemctl start xrdp
```

#### KEY NOTE: 
If there is a desktop environment (GNOME etc) already running, then this will need to be stopped before attempting to remote in. 
Otherwise, the remote client will keep quitting.
