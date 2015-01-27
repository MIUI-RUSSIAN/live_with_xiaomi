# Walking with Devils
How to live with china malware maker's product



Background
====
It is well known China companies making good smartphone HW and malwares. Follow steps in this guide, users can enjoy nice phones without big brother's watching or junk pushing.


Deps
====
* ADB and fastboot. Do not download them from China's ICP's, they are very likely compromised.
* CWM recovery image (6.0.5.1 at the time this is written) for your phone model. WCDMA + LTE, CDMA + LTE and TDSCDMA + TD-LTE model uses different recovery images.
* Google Service Framework and Applications, which is missing in China's smartphones. Check http://forum.xda-developers.com/showthread.php?t=2397942 for further info and download links.
* **optional** BETA-SuperSU-v2.44.zip or latest version for your phone model.

Notes:
* There's absolutely no guaranty, don't blame me for any mess. 
* The following steps are tested on Redmi2/Hongmi2/HM20140811/HM20140813
* It may likely to work on other Xiaomi phones/pads, but neither tested nor guarantied.
* Backup any important data. Something bad always happens.


First Thing First
====
Let's remove some stock malware.

It is **HIGHLY RECOMMENDED** not to
* Connecting WiFi
* Insert SIM/USIM/R-UIM... cards
* Setup e-mail or any other accounts (I saw Email.apk connecting a server in Beijing, even after I typed a fake email/password)

before malwares are removed. Or your privacy might very likely to be sent to **Beijing**.


Flash CWM recovery
----
1. Connect USB cable between phone and PC.
1. Enter FASTBOOT mode by
  1. Power off phone
  1. Hold **`VOL-`** key while power on, until about 2-5 seconds after the nudge.
1. On PC, open a Terminal/Command Prompt window and type:

```
fastboot flash recovery <path-to-recovery.img>
fastboot boot <path-to-recovery.img>
```

>On windoze, you may need to type 'fastboot.exe' instead of 'fastboot'

Now the phone should boot into CWM recovery in 20-30 seconds

Remove Stock Malwares
----
in CWM recovery, keep usb cable connected, mount /system and clear dalvik cache

* On PC, in a Terminal/Command Prompt window, type:
```
adb shell
```
an ADB shell will be running

* remove bad ones, type:
```
cd /system/priv-app
rm Backup.apk Browser.apk CloudAppBackup.apk MiGameCenterSDKService.apk FileExplorer.apk
cd /system/app
rm GameCenter.apk KingSoftCleaner.apk MiAssistant.apk  MiLinkService.apk MiuiSuperMarket.apk MiuiVideo.apk VoiceAssist.apk XiaomiServiceFramework.apk XiaomiAccount.apk Email.apk
```
* also, if you don't like Windoze Style **lite mode**
```
rm /system/\*app/jjhome.apk 
rm /system/\*app/jjsms.apk
```
* Reboot, and if you like, confirm the result using eolwral OSMonitor or something simular.


Root
----
It's pretty easy, but not necessary, neither recommended for non geeks.

1. boot the phone into CWM recovery by
  1. Power off
  1. Press **`VOL+`** button before power up, and hold for several seconds after the nudge
  1. In the bootloader menu, click '''Recovery''' button, the buttons are small, don't miss it.
1. select Install Zip from /storage/sdcard1
1. Flash your SuperSU-x.yz.zip
1. Reboot

Install Google Service Framework and Applications
----
or gapps in short form.
There are many guides available, follow them.


What else?
====
These are very safe to remove, if you don't like them.

File name | Type | Comments
--- | --- | ---
`BugReport.apk`|useless service|
`Backup.apk`|useless service|has too many permissions
`GooglePinyinIME.apk`|IME| replace it with latest stock version
`Galaxy4.apk`|Wallpaper|Live wallpapers? No~
`MagicSmokeWallpapers.apk`|Wallpaper|
`NoiseField.apk`|Wallpaper|
`PhaseBeam.apk`|Wallpaper|
`VisualizationWallpapers.apk`|Wallpaper|
`CloudPrint2.apk`|Print service|
`PrintSpooler.apk`|Print service|
`CameraStability.apk`||really useless
`YellowPage.apk`|Call/SMS blocker|and identifies unknown numbers
`BlockList.apk`|Call/SMS blocker|
`MiuiGallery.apk`||for privacy sake, replace with good ones.
`Music.apk`||I don't like to agree Baidu EULA. replace with good ones.
`MiuiVideo.apk`||ditto
`Weather.apk`||for privacy sake
`WeatherProvider.apk`||ditto
`FileExplorer.apk`||for privacy sake, replace with good ones. This guy also scans local computers!
`Notes.apk`||ditto
`SoundRecorder.apk`||ditto
`Calendar.apk`||Too many permissions
`CalendarProvider.apk`||ditto
`VoiceAssist.apk`||just useless
`MiLinkService.apk`||Do you trust MiLink?
`MusicFX.apk`|Audio EQ|

>Yet more are under test and coming soon.

Hands off
====
Removing these will brick your phone, though they looks real bad. Or if you know how to remove these safely, please let me know.
* SecurityCenter.apk
* Updater.apk


Lose-Lose options
====
These are removable, but at cost of feature loss
* AMAPNetworkLocation.apk, for WiFi/Cellphone Network positioning
* DownloadProvider.apk & DownloadProviderUI.apk, they use Xunlei/Thunder's junk service. But by removing them you will lose PlayStore.
* ThemeManager.apk, without this you cannot setup ringtone or wallpaper



Support me to help you and more people.

Donations of any amount are greatly appreciated!

bitcoin: `1Hy25upwMTZvxUp8RQxg1CposF15bCDxew`
