---
layout: post
title: "Docker Ventures"
---

I've been experimenting with docker lately and thought I'd put my home server to use by self hosting a few apps. 

In this post, I'll describe some of the essential steps/learning that I discovered on route.

## Tip 1 - Use a dashboard
[Heimdall](https://hub.docker.com/r/linuxserver/heimdall) is a fantastic utility for linking to your docker web apps. Previously, the experience of juggling through multiple bookmarks in my browsers was getting tiresome fast. Using Heimdall allows a centralised place on your home network to manage all those links.
Further, using pihole, you can create your own DNS records, such that at my-custom-domain.com will now point to a private IP of your choice.

## Tip 2 - Docker compose is music to my ears
This makes managing apps that require multiple containers/shared networks/shared volumes much simpler.
Bringing apps up/down is just a single command e.g docker compose -up. Running in daemon mode allows apps to be run silently in the background. Further, docker also handles starting these at boot time of the server.

## Tip 3 - Be aware of the fleet
[Linux Server fleet](https://fleet.linuxserver.io) - this provides a wealth of inspiration for apps that can be run on your home server. Your milage may vary but some are really impressive. I'd reccomend photoPrism if you like photography.

## Tip 4 - Containers are emphemeral
Remember, key information is not meant to be left inside a container file system. When in doubt, save that to a volume (on disk that has backups sorted!) or be happy to lose it.

## Tip 5 - Update your docker images
Honesty moment - I haven't automated this yet. [Watchtower](https://containrrr.dev/watchtower/) is designed for automating the update of your docker images. This can cause more harm than good, but at the same time, running off ancient versions of something is never a good idea.

## Tip 6 - Docker compose stop & docker compose down are NOT the same
stop brings your container to a hault, where as down will remove the containers, networks etc (remember containers are emphemeral right?). This reminds me, for complex apps like photoprism which require many hours of processing to build up the database/complete indexing on faces etc - this will need to be upgraded with care to avoid having to repeat all that compute time.

## Tip 7 - Use official repo (docker hub) and avoid privileged running where possible
I've avoided running priviledged at all costs so far, but w.r.t docker hub - I have made use of some other repos. 

## Tip 8 - If using truenas scale - take a look at TrueCharts
There's abuntance of scale compatible images available for TN scale here. I'm not overly keen on running too much on my nas, but it's nice to know there are options.

## Bonus
I did try running Ubuntu in a container and accessing via Microsoft remote desktop. I was able to connect but didn't get to explore very far. 
