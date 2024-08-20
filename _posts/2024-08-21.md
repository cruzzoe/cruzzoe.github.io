---
layout: post
title: "Creating fileshares from Truenas"
---

When having multiusers in truenas, there are 2 type of permissioning that can be set up for Samba:

1. Share ACL
2. Filesystem ACL

the first one is defaulted to everyone and so can be left alone.

the second one is a bit more fiddly. We must control here to ensure that the correct permissions are reflected.

It's often useful to mount the share for example on a raspberry pi.

I think it's necessary to have the uid/gid mapped correctly to ensure compliance.

Also note, when mounting the share, the share will often be mounted as root. this means the user on the pi cannot write to the share.

To resolve this, use the correct uid/gid from the pi user name to mount the share. It should now work
