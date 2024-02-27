---
layout: post
title: "The joy of incremental backups"
---

## Introduction
Entrusting your data to multiple devices is paramount to data security. However, if your master copy is accidently deleted, modified beyond repair etc, then all your data will feed through to your backup devices. 
Instead of using this approach, we can benefit from incremental backups.
 
This works by copying a delta of only the changed files to the backup repo, similar to how git works. Then, should we want to view the state of the world as of a particular timestamp, we can easily retrieve this.

## Encryption

Do you a) trust your cloud provider? b) have confidence that your cloud will not be hacked?

Both a & b are impossible to have complete confidence. Instead of depending on your provider, encrpyting at source is the way to go. This way, your encryption key never leaves your device and so even if the cloud is comprimised, your data is safe.
Obviously you need to make sure you keep a handle on your encryption keys!

## Links
Two tools that I've been using:

https://www.borgbackup.org/
https://torsion.org/borgmatic/

Borgmatic is a wrapper around borgmatic to help manage the configuration/running of borg backup.

## Key takeway
Incremental backups ensure should you accidently rm -rf * all your important files (& not immediately notice). You can still survive the data loss & go back in time to any particular timepoint. 
