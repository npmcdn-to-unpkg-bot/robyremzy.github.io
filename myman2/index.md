---
layout: page
title: Android My Man
modified: 2015-01-03T13:37:00.362000-04:00
excerpt: "Instructions on how to install and customize your Android"
image:
  feature: Android_Pattern_green1.jpg
  credit: Psychopulse
  creditlink: http://psychopulse.deviantart.com/
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Overview</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->








# Philosophies, ROM AOSP & App
First please if you want to do some mod inside your phone you may want to read this:  
[Custom ROMs For Android Explained - Here Is Why You Want Them](http://www.androidpolice.com/2010/05/01/custom-roms-for-android-explained-and-why-you-want-them/)  

*In short who is behind OmniROM:*  
XplodWild, the man behind Focal and an ex-CyanogenMod team member, has announced at the Big Android BBQ that he and other highly talented Android developers like Chainfire (SuperSu developer), Dees_troy (TWRP developer), Pulser, Entropy and Andrew are working together on OmniROM. [source](http://www.androidbeat.com/2013/10/omnirom-ex-cyanogenmod-brings-multi-window-roadrunner-more/)

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

___________  

## OmniROM Impressions

<p><a href="https://commons.wikimedia.org/wiki/File:Android_4.4.2.png#mediaviewer/File:Android_4.4.2.png"><img alt="Android 4.4.2.png" src="https://upload.wikimedia.org/wikipedia/commons/c/c7/Android_4.4.2.png" height="480" width="270"></a>

<a href="http://imgur.com/nGUJjsl"><img src="http://i.imgur.com/nGUJjsl.jpg" height="480" width="270"></a>

</p>



### User interface alias Launcher
OmniROM use the AOSP Launcher call **Laucher3**, good enough and lightweight,but not so slick. I couldn't help it and after a while i did put **Nova Laucnher** as my default UI, to check or install, Nova Laucher; go to their [WebSite](http://novalauncher.com/), and download it from there directly. I found it a li'l more pitchy but i did say good bye to some Ram there.  
<p><a href="http://imgur.com/56Ay4A2"><img src="http://i.imgur.com/56Ay4A2.png" height="57" width="350"></a></p>

### Omni Features
As Google Now, OmniROM is about to take it one step further with the Custom launcher [hotwords](http://omnirom.org/features/custom-hotwords-home-screen/), soon on [OmniROm nightlies](http://omnirom.org/downloads/), i keep an eye on it.  

___________

The fancy [OmniSwitch](http://omnirom.org/features/easily-switch-apps-omniswitch/) witch provide quick access to whatever you want to and also deliver the [multi windows](http://omnirom.org/features/easily-switch-apps-omniswitch/), imo it's challenging but i don't use that, so i try it but switch it off after 4 hours.  

___________

The things very neat was the lightweight, and full open and secure, OTA system update, i really feel like i was on my Nexus 7 (2013) with OTA updates, but here for all the nightlies, so pretty much often! When it pop-up - click install and it reboot on TWRP recovery make your update and voilà! ladida! Really appreciate that thanks.

___________

The open source Omni Installer work well, i use F-droid tho, but when i have to use it with some random .apk it do the job well.

___________

The Non-intrusive call notification, is very awesome, and i fell like i don't have to download a third party app to switch my dialer app. In general the Stock SMS app is very good, with a lot of settings as well as the Stock Dialer app, i rather not use a a third party dialer, contact or SMS app, and for now i'm actually happy with Omni Stock app.  
<p><a href="http://imgur.com/pfiSpKC"><img src="http://i.imgur.com/pfiSpKC.png" height="116" width="350"></a></p>

___________

I use several language on my Keyboard and OmniROM use the **Android Keyboard (AOSP)**, witch is fine for me right now, i just have to go down the menu `Settings/Input Languages` I checked Spelling corrections and set it as the system languages. In **Keyboard & Inputs Methods** down in Android Keyboard (AOSP) check the settings, and UNCHECK System Languages and select the languages you want. Then, when you will be prompt to type with your keyboard you can click on the *earth* logo witch will let you select your personal languages inputs methods.

**Fonts Tips:** I should check the Fonts, it seems different, i will try to see if i can use  
[source-sans-pro](https://github.com/adobe-fonts)  
[Noto Sans](http://www.google.com/fonts/specimen/Noto+Sans)  
[Droid Sans](http://www.google.com/fonts/specimen/Droid+Sans)
{: .notice}

___________


I will not get through all spec and features and i will stop here my quick test.
To check on some specific app or alternative as Google check here for more [Apps Test](http://robyremzy.github.io/myman/android2)

___________


#### Quick report
**Android** version 4.4.4 **Omni** Version 4.4.4-20150102-Nightly  

The device GS3 i9300:

+   very Hot very quick!
+   Several crash while messing around with camera or on scroll with multiple Apps?
+   Battery drain quick 6 Hours on hardcore use!
+   TODO a drain battery test.

<p><a href="http://imgur.com/9RDnhM9"><img src="http://i.imgur.com/9RDnhM9.png" height="127" width="350"></a></p>
<br>
<br>
**Android** version 4.4.4 **Omni** Version 4.4.4-20150103-Nightly  

The device GS3 i9300:  

+   Is that me or it's more stable!
+   Humm it did crash during a +45min call
+   Still heat quick

being update...
