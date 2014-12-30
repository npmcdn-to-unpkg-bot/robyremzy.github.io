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


# Philosophies, ROM AOSP & App
First please if you want to do some mod inside your phone you may want to read this:  
[Custom ROMs For Android Explained - Here Is Why You Want Them](http://www.androidpolice.com/2010/05/01/custom-roms-for-android-explained-and-why-you-want-them/)  

## Install ROM AOSP
So, for different reasons (CEO Dumb Ass spoted) i expect to change my Custom ROM from "Cyanogen" to "[OmniRom](http://omnirom.org/)", and move my bootloader from ClockWorkMod to [TWRP](http://forum.xda-developers.com/showpost.php?p=32964275&postcount=1).
Here a simple HowTo trying to resume my steps from that switch:  

-     **DOWNLOAD** TWRP for [Samsung Galaxy S3](http://teamw.in/project/twrp2/) (International i9300) [i9300]
-     **DOWNLOAD** SuperSU CWM / TWRP / MobileODIN [installable ZIP](http://download.chainfire.eu/supersu) from ChainFire
-     **DOWNLOAD** the [OFFICIAL Up-to-Date PA-GOOGLE APPS](http://forum.xda-developers.com/showthread.php?t=2397942) from Paranoid if you want to use Google Apps
-     **DOWNLOAD** the last OmniROOM available for [Samsung Galaxy S3](http://dl.omnirom.org/i9300/)

You should now have 1 .img and 3 .zip files ready to be "flash" on your phone let's see how to do that with swag.  


You need FIRST to **INSTALL** or "flash" TWRP on GNU/LINUX OS  
Activate the USB DEBOGGED by going to Parameters/About Phone/ hit 4 times on Build number at the very bottom, then check USB DEBOGGED into Parameters/{}Dev Options.
Reboot your phone on « download » MOD by pushing Volume down,home, and power all at same time during a while.  
Plug your phone on USB to your computer  
Open a Terminal CRTL ALT +T  and copy that:  

{% highlight bash %}
sudo apt-get install heimdall-flash
sudo heimdall flash --RECOVERY openrecovery-twrp-2.8.3.0-i9300.img --no-reboot
{% endhighlight %}

Wait for the full blue bar and all verbose to be complete from the Term.  
Then unplug you USB and reboot on recovery MOD by pushing volume UP, home, and power all at same time during a while or in apps.  

**NB:** You just Installed TWRP as a new bootloader, now you should immediately reboot on recovery MOD.  


In a SECOND TIME your are on recovery MOD,  
From the Menu choose **Wipe** and do a **factory reset**  
From the Menu choose now **Install**  
Go find the custom ROM file.zip and select it, you can select and 2nd zip in queue choose the SuperSU.zip  
You can even choose a 3rd file to be on queue but i past on the PA-GOOGLE APPS, i'm Google less now.  
Hit Install, and wait.  

You did reboot automatically on your fresh new ROM.  
BUT, I did an extra step after reboot on OmniROM,  
I shut down the phone again.  
Reboot on recovery MOD  
From the Menu choose **Wipe** and do a all data format (but not the MicroSD Card) and reboot.
Now it's very clean on OmniROM.  

## Install Apps

***APP NB: Download Priority Order:***  

+     [**F-Droid**](https://f-droid.org/)  
+     [GitHub](https://github.com/) or Home Website  
+     [XDA package](http://forum.xda-developers.com/)  
+     [googleplaydownloader](https://codingteam.net/project/googleplaydownloader)  
+     GooglePlay Store as *evosi*  

You can also download apps from there [apps.evozi.com/apk-downloader](http://apps.evozi.com/apk-downloader/)  

**NB: From the Menu security/settings choose Allow Install from Unknown source**  
You can acces some usefull information on the Menu Parameters/Status, like your phone number, IP or MAC address ect...

### CalDAV and CardDAV
For all this kind of Sync as Contact & calendar it's done from my own server, and i use DAVdroid for that remote access [Hot To Sync From CozyCloud](http://cozy.io/mobile/contacts.html).  

[DAVdroid](http://davdroid.bitfire.at/what-is-davdroid)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=at.bitfire.davdroid)  


For now a descent [Calendar Widget](https://github.com/plusonelabs/calendar-widget)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.plusonelabs.calendar)  
*need help to change calendar color, and not have all cal in same color Sync [contacts](http://cozy.io/mobile/contacts.html) *need help to sync pics and gps and a simple option for Facebook birthday com.anydo.cal*





### Texting & SMS  
[TextSecure](https://github.com/WhisperSystems/TextSecure)  
*NB: for compatibility with iOS see [here](https://github.com/WhisperSystems/Signal-iOS)*  




### Explorer  
[Amaze File Manager](https://github.com/arpitkh96/AmazeFileManager)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.amaze.filemanager)  

[AntTek Explorer Ex]()
[![XDA](https://pbs.twimg.com/profile_images/514806075132895232/HU2Ar_rW_normal.jpeg)](http://forum.xda-developers.com/showpost.php?p=44678595&postcount=1)  
[SafeBox]()
[![XDA](https://pbs.twimg.com/profile_images/514806075132895232/HU2Ar_rW_normal.jpeg)](http://forum.xda-developers.com/showpost.php?p=57393874&postcount=1)




### Edition  
[Turbo Editor](https://github.com/vmihalachi/turbo-editor/blob/master/README.md)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.maskyn.fileeditorpro)  
[Quoda](http://www.getquoda.com/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.henrythompson.quoda)  
[WPS Office Kingsoft Offfice](http://www.wps.com/support/) ON [WebSite](http://www.wps.com/android/)  


### Key Ring  
[KeePassDroid](http://www.keepassdroid.com/)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.android.keepass)  



### Mail Client
To be able to use PGP on K-9Mail you need to install [AGP](http://thialfihar.org/)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=org.thialfihar.android.apg)  

[K-9 Mail](https://github.com/k9mail/k-9/wiki)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.fsck.k9)  
**NB: Rulez for [IMAP/SMTP](http://www.arobase.org/messageries/serveurs.htm) configuartion**  
**NB2: To install a Google email account, manage your app passwords, please visit**  
[https://security.google.com/settings/security/apppasswords?rfr=aem](https://security.google.com/settings/security/apppasswords?rfr=aem)  




[Tutanota](https://github.com/tutao/tutanota) on [Google](https://play.google.com/store/apps/details?id=de.tutao.tutanota)

____  
**Steel Testing Skype Alternatives**  
____  
**XMPP / Jabber**  
Get a new JID by following that [tuto](https://duck.co/blog/using-pidgin-with-xmpp-jabber)  
[XMPP-Conversation](https://f-droid.org/repository/browse/?fdid=eu.siacs.conversations)  
[XMPP-Xabber](https://f-droid.org/repository/browse/?fdid=com.xabber.androiddev)  
Ces clients peuvent necessiter l'installation de [Orbot](https://f-droid.org/repository/browse/?fdid=org.torproject.android) et [OpenKeychain](https://f-droid.org/repository/browse/?fdid=org.sufficientlysecure.keychain)  
____  
**ToX**  
Tox Client Android [Antox](https://wiki.tox.im/Binaries#Android_.28Warning:_Deprecated.29)
____  
**WebRTC Conferencing**  
[MegaChat](http://kim.com/)  
[Firefox Hello](https://support.mozilla.org/en-US/products/firefox/firefox-hello-webrtc)  
___  

## Browser
### web
[Firefox](https://www.mozilla.org/en-US/firefox/new/?icn=tabz)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=org.mozilla.firefox)

[DuckDuckGo](https://duck.co/)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=se.johanhil.duckduckgo)

### Lecteur RSS
[NewsJet](http://newsjet.mobi/)
[![XDA](https://pbs.twimg.com/profile_images/514806075132895232/HU2Ar_rW_normal.jpeg)](http://forum.xda-developers.com/showpost.php?p=47764077&postcount=1)  

### Reddit
[**Flow for Reddit--Pre-Beta**](https://www.reddit.com/r/RedditFlow/new/) ON
[GooglePlay](https://play.google.com/store/apps/details?id=com.deeptrouble.yaarreddit)  
[reddit sync](https://www.reddit.com/r/redditsync/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.laurencedawson.reddit_sync)  
[reddit.iama](https://www.reddit.com/r/redditmobile) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.reddit.iama)  

### Twitter  
[Falcon Pro](http://getfalcon.pro/) ON WebSite with [help here](http://www.androidpolice.com/2013/07/03/falcon-pro-updates-to-v2-0-4-outside-of-the-play-store-now-supports-a-way-to-blatantly-skirt-twitters-token-limit/)  

## Music Video

[VLC](http://git.videolan.org/?p=vlc-ports/android.git;a=summary)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=org.videolan.vlc)  

[SnapTube](http://www.snaptubevideo.com/)
[![XDA](https://pbs.twimg.com/profile_images/514806075132895232/HU2Ar_rW_normal.jpeg)](http://forum.xda-developers.com/showpost.php?p=57592125&postcount=1)  

[PopcornTime](http://popcorntime.io/) ON [WebSite](http://popcorntime.io/)  

[SoundCloud](https://soundcloud.com/mobile) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.soundcloud.android)  
[Shazam](http://www.shazam.com/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.shazam.android)  
[Groovshark](http://grooveshark.com) ON [WebSite](http://mobile.grooveshark.com/phones)  
[GSRemote for Grooveshark](http://gsremote.com/) ON [GooglePlay](https://play.google.com/store/apps/details?id=uk.co.awesomedigital.gsremote)  
[Crunchyroll - Anime and Drama](http://www.crunchyroll.com/devices#android) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.crunchyroll.crunchyroid)  






### Sync 'n Cloud
[Syncthing](https://ind.ie/pulse/)  
see on [GitHub](https://github.com/syncthing/syncthing-android)  
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.nutomic.syncthingandroid)  

GitHub  
Owncloud  
CozyCloud  
[Moon+ Reader](http://www.moondownload.com) ON [WebSite](http://www.moondownload.com/download.html)  
[Perfect Viewer](https://sites.google.com/site/rookiestudio/) ON [WebSite](https://sites.google.com/site/rookiestudio/xia-zai)  

[CamScanner](https://www.camscanner.com/user/download) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.intsig.camscanner)  
[TVShow time](http://www.tvshowtime.com/en) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.tozelabs.tvshowtime)  
[IMDB](http://www.imdb.com/apps/?ref_=nb_app) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.imdb.mobile)  
[Wish Pocket](http://wishpocket.co.kr/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.skplanet.wishpocket)  
[QuickPic](http://www.alensw.com/en/) ON [WebSite](http://www.alensw.com/en/#download)  
[Duolingo](https://www.duolingo.com/mobile) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.duolingo)  

### Social media
[Diaspora Webclient](https://github.com/voidcode/Diaspora-Webclient)
[![F-Droid](https://lh5.googleusercontent.com/-zezQqsBye0c/VCUpPVjcKEI/AAAAAAAAAIQ/HbcG5f1qMIw/w129-h45-no/getitonfdroid.png)](https://f-droid.org/repository/browse/?fdid=com.voidcode.diasporawebclient)  
[Viber](http://www.viber.com/#android) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.androidbook.ToltecEnergyPrices)  
[SnapChat](https://www.snapchat.com/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.snapchat.android)  
[Vine](https://vine.co/) ON [GooglePlay](https://play.google.com/store/apps/details?id=co.vine.android)  

### Camera
[GoogleCamera](https://play.google.com/store/apps/details?id=com.google.android.GoogleCamera)  


### Tool
[RealCal](http://www.quartic-software.co.uk) ON [GooglePlay](https://play.google.com/store/apps/details?id=uk.co.nickfines.RealCalc)  
[Bright Weather](http://levelupstudio.com/en/brightweather-android) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.levelup.brightweather)  
[OpenVPN Connect](http://www.vpngate.net/en/howto_openvpn.aspx#android) ON [GooglePlay](https://play.google.com/store/apps/details?id=net.openvpn.openvpn)  
[Pixlr-o-matic](https://pixlr.com/mobile) ON [GooglePlay](https://play.google.com/store/apps/details?id=pixlr.OMatic)  
[Pixlr](https://pixlr.com/mobile) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.pixlr.express)  
[Wifi Analyzer](http://a.farproc.com/wifi-analyzer) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.farproc.wifi.analyzer)  
[Toltec Energy](http://www.oktoltecgroup.com/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.androidbook.ToltecEnergyPrices)  
[Instructables](http://www.instructables.com/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.adsk.instructables)  
[Ligue de Football Professionnel](http://www.lfp.fr/) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.netcosports.andlfp)  
[Urban Dictionary](http://www.urbandictionary.com) ON [GooglePlay](https://play.google.com/store/apps/details?id=com.urbandictionary.android)
