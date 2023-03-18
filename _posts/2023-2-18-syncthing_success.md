---
layout: post
title: "Success with Syncthing"
---

I’ve started evangelizing about how amazing Syncthing is. It’s similar to DropBox in that it mounts on your server/laptop/phone a directory where it utilises OS file watching. When it detects a change to a file/new file added/removal of file, it notifies remote clients to replicate the change. 

The big differences comparing Syncthing to Dropbox is that it’s:
- Open source
- Using only your storage. There is no central cloud storage tying everything together

It works on:
- Windows
- Ubuntu
- Android
- Truenas

My plan is to use it to sync up photos, books, audiobooks, music and no longer have to deal with mounting my phone to a desktop and navigating around the android file system.

# File versioning
This is similar to revision history in Dropbox. It is configurable, but in a nutshell it allows you to ‘undelete’ files or restore older versions.

# Relays
Crucially, syncthing doesn't just work on LANs. It works over the internet also! Now, this can be achieved by port forwarding to allow desktop A to connect directly to phone B over the internet, but of course that’s often not possible on networks you don’t own. To achieve connectivity, syncthing can achieve connectivity via the use of relay servers. These range from pretty quick, to terribly slow. At the time of writing this post, there were 426 relays online. 

The data is sent over the relay and is end-to-end encrypted. Essentially, the relay is like a discovery server.

# Access to the UI
Syncthing allows you to configure it via a web UI. This runs on 127.0.0.1 and so is not accessible when running on a headless server. To access the configuration UI you can use SSH tunneling:

```ssh -L 8386:localhost:8384 <user>@server-ip```

# Autostarting the service
To run the service on Ubuntu automatically, systemd is used. Systemd has become the default init system for many modern Linux distributions, including Red Hat Enterprise Linux, Fedora, Debian, Ubuntu, and many others. 

This is configured by unit files which live on the file system.
To interact with systemd the following comands can be used:

```
- Show all running services:
    systemctl status

- List failed units:
    systemctl --failed

- Start/Stop/Restart/Reload a service:
    systemctl start|stop|restart|reload unit

- Show the status of a unit:
    systemctl status unit

- Enable/Disable a unit to be started on bootup:
    systemctl enable|disable unit

- Mask/Unmask a unit to prevent enablement and manual activation:
    systemctl mask|unmask unit

- Reload systemd, scanning for new or changed units:
    systemctl daemon-reload

- Check if a unit is enabled:
    systemctl is-enabled unit
```
