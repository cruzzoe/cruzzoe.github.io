---
layout: post
title: "Archiving a website with wget"
---

To keep a local copy of an entire website such that you can self host use the following command:

`wget --recursive --no-clobber --page-requisites --html-extension --convert-links --restrict-file-names=windows --domains domain.com--no-parent domain.com`

Note, ensure you have permission to do this first.
