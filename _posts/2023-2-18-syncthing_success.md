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
