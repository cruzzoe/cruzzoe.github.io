---
layout: post
title: "BAD SECTOR JUMP"
---

This week my synology nas alerted me to a reallocated sector jump. It went from zero to 32 overnight. 

*“Reallocated sectors are bad sectors on your hard drive that have been moved to another part of the disk”* See [https://harddrivegeek.com/reallocated-sector-count/](https://harddrivegeek.com/reallocated-sector-count/)

Overall, there is a lack of clarity online about how significant a reallocated sector is for the life of a drive. Some of the reading I did indicates that this is just part of how drives work and as long as 
- a) the amount of bad sectors is not growing
- b) Its relatively small then you should be fine. 
- 
- However, I also came across a lot of opinions online that indicate any bad sectors means the drive is on the way out. I decided to go with caution and replace.

This was accepted without fuss by scan.co.uk as part of an RMA but it drives home the importance of a backup strategy and having planned steps for data restoration.

Incidentally, nas drives have a longer warranty period than standard desktop drives. Typically, harddrives last around 3 to 5 years, but if they’re going to fail - this tends to be either at the beginning of life span or the end.

### Automating smart checks
What saved me here was the automated smart check alert from synology otherwise this would have gone undetected. OpenmediaVault alerting on smart issues appears a little flaky. A future project I’d like to undertake is to schedule smart checks manually via smartctrl and setup alerting should the results be sub-par.

### Erasing data before RMA
I used seaTools to erase my data from the drive before sending back for RMA. I used secure erase with over-writes. I couldn’t find any studies on how effective this delete is but am hoping seagate know what they’re doing here and my data isn’t of national security importance…

### Reading data from windows from Synology drive
The drive was part of SHR-1  (Synology hybrid raid with no redundancy). My understanding is this is formatted in ext. Out of curiosity, I tried to access the data from my windows PC. To do this I used wsl2 running Ubuntu following this guide: [https://learn.microsoft.com/en-us/windows/wsl/wsl2-mount-disk](https://learn.microsoft.com/en-us/windows/wsl/wsl2-mount-disk) This however didn’t work and I think it’s related to the fact the disk was part of a raid array (SHR). I found a synology KB page [https://kb.synology.com/en-my/DSM/tutorial/How_can_I_recover_data_from_my_DiskStation_using_a_PC](https://kb.synology.com/en-my/DSM/tutorial/How_can_I_recover_data_from_my_DiskStation_using_a_PC) which seemed more promising and detected the device path: /dev/vg1000/lv however this also refused to mount. 

In the end, I gave up trying to access the data as I had it all backed up anyway, but it makes me reluctant to use Raid in future. I’ll stick to using basic disk instead for reduced complexity.

### Lessons learned for the future
Ensure that drive health checks are regular, working & that someone is doing something should they fail
Plan for failure. At around 3-5 years, plan to switch out drives. Obviously, the drives could fail at any point but replacing drives on a schedule should avoid additional ‘surprises’.
Test your backups. From my previous post about how to automate backups, I realised I had no alerting on this. Should the backup fail from my cron job - then something needs to happen. 
Off-site backups. I never thought I’d get bad sectors the week after I wrote about data backups. But that’s life. Fire/theft/water-damage/power-surges/breached network are all unlikely but possible. We should plan for this if we’re keen to keep hold of our data.

### Further thoughts on data loss
- It would be interesting to have an algorithm/calculator to determine the ‘value’ of your data. This should factor: 
- how long did the data take to obtain. If 50 hours was spent procuring the data, how much is your time worth if losing data is acceptable? 
- Can the data be replaced? E.g personal photos. Chances are not.
- Disruption to BAU activities e.g work/medical. Opportunity costs exist here
- Financial loss. E.g products you’ve bought that can be rebought (at cost)
