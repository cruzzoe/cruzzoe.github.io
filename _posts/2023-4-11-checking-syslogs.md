---
layout: post
title: "Troubleshooting failure on linux"
---

Short tip for tracking down the failure on a linux host.

`sudo journalctl  -b -1 -e` 

This shows the syslog right up until the moment that the machine got restarted.

## A quick summary:

The sudo journalctl -b -1 -e command is used to view the system logs for the previous boot session on a Linux system. Here's what each part of the command does:
* journalctl: The command to view system logs on Linux.
* -b: Show logs from a specific boot session. In this case, it shows the logs from the previous boot session.
* -1: This option is used with the -b option to specify the boot session number. -1 means the previous boot session.

* -e: Show the end of the logs. This option is used to show the most recent log entries first.

So, when you run sudo journalctl -b -1 -e, you will see the system logs for the previous boot session, starting with the most recent log entries and ending with the earliest ones. 

This can be useful for troubleshooting issues that occurred during the previous boot session.
