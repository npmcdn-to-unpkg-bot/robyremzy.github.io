---
layout: post
title: "What Phone is dat!"
modified:
categories:
excerpt: "Set-Up of my phone"
tags: [Android]
image:
  feature:
date: 2014-12-28T19:23:42+01:00
---

## Install ROM AOSP
So, for different reasons (CEO Dumb Ass spoted) i expect to change my Custom ROM from "Cyanogen" to "[OmniRom](http://omnirom.org/)", and move my bootloader from ClockWorkMod to [TWRP](http://forum.xda-developers.com/showpost.php?p=32964275&postcount=1).
Here a simple HowTo trying to resume my steps from that switch:  

-     **DOWNLOAD** TWRP for [Samsung Galaxy S3](http://teamw.in/project/twrp2/) (International i9300) [i9300]
-     **DOWNLOAD** SuperSU CWM / TWRP / MobileODIN [installable ZIP](http://download.chainfire.eu/supersu) from ChainFire
-     **DOWNLOAD** the [OFFICIAL Up-to-Date PA-GOOGLE APPS](http://forum.xda-developers.com/showthread.php?t=2397942) from Paranoid to use Google Apps
-     **DOWNLOAD** the last OmniROOM available for [Samsung Galaxy S3](http://dl.omnirom.org/i9300/)

##### You should now have 1 .img and 3 .zip files ready to be "flash" on your phone let's see how to do that with swag.  
Pre Step

+   Activate the **USB Debugging** go to Settings/System - About Phone/ hit 4 times on Build number at the very bottom, and then check USB Debugging into Settings/System - {}Dev Options.

**INSTALL** or "flash" TWRP **with** GNU/LINUX OS

+   Reboot your phone on **download MOD** by pushing **Volume down,home, and power** all at same time during a while.  
+   Plug your phone on USB to your computer  
+   Open a Terminal CRTL ALT +T  and copy that:  


{% highlight bash %}
sudo apt-get install heimdall-flash
sudo heimdall flash --RECOVERY openrecovery-twrp-2.8.3.0-i9300.img --no-reboot
{% endhighlight %}

___________  

*Wait for the full blue bar and all verbose to be complete from the Term.*  

___________  

**NB:** You just Installed TWRP as a new bootloader, now you should immediately reboot on recovery MOD. Unplug you USB and reboot on **recovery MOD** by pushing **volume UP, home, and power** all at same time during a while or in apps.  

___________

Your are now on **recovery MOD**  

+   From the Menu choose **Wipe** and do a **factory reset**  
+   From the Menu choose now **Install**  
+   Go find the **custom ROM file.zip** and select it, you can select and 2nd zip in queue choose the **SuperSU.zip**  
+   You can even choose a 3rd file to be on queue but i past on the **PA-GOOGLE APPS.zip**, i'm Google less now.  


*Hit Install, and wait.*  

##### You did reboot automatically on your fresh new ROM.  

**PRO Tips:** I did an extra step after the 1st reboot on OmniROM,  
I shut down the phone again.  
Reboot on recovery MOD  
From the Menu choose **Wipe** and do a all data format (but not the MicroSD Card) and reboot.  
Now it's a **very clean OmniROM**.  
{: .notice}

**Hipster Tips:** the easter egg of the Android version is at  
**Settings/About Device/**  
click several times on **Android Version**  
repeat the several click on the picture too!  
{: .notice}
