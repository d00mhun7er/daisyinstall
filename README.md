A noob guide to install custom ROM on Mi A2 Lite. All credit goes to @XDA, @tkchn 
and the respective developer of the custom ROM who contribute so much to 
the community. I simply created this guide to documenting all of 
the process and steps taken by me to get the job done based 
on various sources around Internet, especially from @XDA
and @tkchn.

# Noob guide to install custom ROM on Mi A2 Lite.
### This guide can be applied to the other smartphone that have the same A/B partition layout as Mi A2 Lite with few adjustment.
#### https://www.xda-developers.com/how-a-b-partitions-and-seamless-updates-affect-custom-development-on-xda/
#### *All credit goes to @XDA, @tkchn and the respective developer of the custom ROM who contribute so much to the community.*

## Pre-requisites, download all
1.  ADB and Fastboot from here: https://www.xda-developers.com/google-releases-separate-adb-and-fastboot-binary-downloads/
2.  TWRP Daisy image:           https://androidfilehost.com/?fid=6006931924117887098
3.  TWRP Daisy zip:             https://androidfilehost.com/?fid=6006931924117887097
4.  ForceEncryption disabler:   https://forum.xda-developers.com/attachment.php?attachmentid=4704479&stc=1&d=1550012491
5.  Custom ROM and Gapps:
* GSI Android Q:    https://forum.xda-developers.com/mi-a2-lite/development/10-0-android-q-daisy-t3967734
* LineageOS:        https://forum.xda-developers.com/mi-a2-lite/development/lineageos-16-0-xiaomi-mi-a2-lite-t3919060
* Resurrection:     https://forum.xda-developers.com/mi-a2-lite/development/9-0-resurrection-remix-v7-0-2-xiaomi-mi-t3926922
* SuperiorOS:       https://forum.xda-developers.com/mi-a2-lite/development/9-0-superioros-xiaomi-mi-a2-lite-t3946434
* POSP:             https://forum.xda-developers.com/mi-a2-lite/development/9-0-potato-sauce-project-laciachan-t3953159
* AOSIP:            https://forum.xda-developers.com/mi-a2-lite/development/9-0-aosip-rom-t3929596
* ViperOS:          https://forum.xda-developers.com/mi-a2-lite/development/9-0-viperos-v6-3-xiaomi-mi-a2-lite-t3927195
* CrDroid:          https://forum.xda-developers.com/mi-a2-lite/development/crdroid-v5-3-xiaomi-mi-a2-lite-daisy-t3922508
* Bootleggers:      https://forum.xda-developers.com/mi-a2-lite/development/9-0-bootleggers-xiaomi-mi-a2-lite-t3954432
* AICP:             https://forum.xda-developers.com/mi-a2-lite/development/android-ice-cold-project-t3922513
* Paranoid Android: https://forum.xda-developers.com/mi-a2-lite/development/paranoid-android-pie-beta-xiaomi-mi-a2-t3912880
* Open GApps:   https://opengapps.org/


## WARNING!
REMOVE ALL THE PIN, FINGERPRINT, LOCK PATTERN AND PASSWORD on the device before proceed to install custom ROM.
USE THE USB DATA CABLE to connect your phone with the computer.


## Unlock the bootloader
(Unlock the bootloader will erase all of your data by default, so be sure to backup first all the necesssary data. )
> *p/s: Hold down volume key when execute the command wil not erase your data.*

1.  Enable OEM Unlocking and USB Debugging in Developers Option.

2.  Extract adb_fastboot zip file, open command prompt / powershell inside the extracted file, I use powershell:
    > PS C:\Users\NyahKauDariSini\Downloads\CustomROM\adb_fastboot>

2.  Type the command:
    > adb reboot booloader
    
    * `daemon not running; starting now at tcp:5037`
    * `daemon started successfully`

4.  If you encounter driver problem, open 'Device Manager'. Unplug the USB cable and plug it back, then right-click 'Update Driver' > 'Search Automatically For Updated Driver Software'. It should do the trick to install missing driver, in my case it is Android Bootloader Interface.

5.  Type the command:
    > fastboot oem unlock
    
    * `< waiting for any device >`
    * `OKAY [  0.012s]`
    * `Finished. Total time: 0.025s`


## Install custom recovery TWRP
1.  Copy all the pre-requisites stuff into adb_fastboot folder.
    (TWRP Daisy image with zip, custom ROM, ForceEncryption disabler and gApps)

2.  Type the command:
    > fastboot boot .\twrp-daisy-3.3.1-0-offain.img
    
    * `Sending 'boot.img' (37436 KB)   OKAY [  0.858s]`
    * `Booting                         OKAY [  0.720s]`
    * `Finished. Total time: 1.789s`

3.  You will see the TWRP recovery on your phone, prompting to enter the password. Choose "Cancel"


## Install custom ROM
1.  In the main menu, choose "Wipe", then tap "Format Data". Type "yes"

2.  Go back to main menu, choose Advance Wipe, then tick:
    * System
    * Data
    * Dalvik/ART cache

3.  Swipe right to wipe.

4.  On your computer, copy all the pre-requisites you've downloaded earlier to the phone. In this case using adb:
    > adb push .\AOSiP-9.0-Pizza-daisy-20190613.zip .\open_gapps-arm64-9.0-nano-20190630.zip .\twrp-installer-daisy-3.3.1-0-offain.zip .\disforsenc_daisy__zero.zip /external_sd

    * `\AOSiP-9.0-Pizza-daisy-20190613.zip: 1 fil...hed. 29.3 MB/s (426126306 bytes in 13.881s)`
    * `.\open_gapps-arm64-9.0-nano-20190630.zip: 1...shed. 29.4 MB/s (174558241 bytes in 5.666s)`
    * `.\twrp-installer-daisy-3.3.1-0-offain.zip: ...ushed. 30.9 MB/s (17521216 bytes in 0.540s)`
    * `.\disforsenc_daisy__zero.zip: 1 file pushed. 23.9 MB/s (839216 bytes in 0.034s)`
    * `4 files pushed. 29.3 MB/s (619044979 bytes in 20.137s)`

5.  On your phone, tap "Install" and flash the files in the following order:
    * Custom ROM
    * TWRP ZIP
    * ForceEncryption Disabler

6.  Don't install Magisk, GApps or anything else yet, we will do that later!

7.  After everything is done, DON'T TAP REBOOT YET. Instead, go back to the main menu, choose "Reboot", change the slot.
    (E.x. if it says "Current Slot: A", tap "Slot: B", vice versa.)
    
8.  Quit the menu and tap "Recovery" in the reboot menu. Copy all the good stuff that you want to install on your phone 
    (Magisk, Gapps, modules, etc.) and flash it the usual way. Reboot your phone.


##     Q & A 
###    1. My phone bootloop. What should I do?
       Hard reset. At least that worked for me.
        
###    2. How do I hard reset my Mi A2 Lite?
       Turn off the phone. Press Power + Volume Up simulatenously.
        
###    3. How to enter bootloader?
       Turn off the phone. Press Power + Volume Down simulatenously.
       
###    4. I use Ressurection Remix but every time I reboot back to recovery it go straight to RR recovery, not TWRP recovery! (I LOST MY TWRP RECOVERY)
       Reboot the phone back to fastboot mode using this command:
       > adb reboot bootloader
       
       Then, boot back to the twrp image using this command (boot back to twrp recovery for just ONCE.):
       > fastboot boot .\twrp-image-path.img
       
       After that, locate the twrp.zip file in internal storage / external_sd and flash it.       
       p/s: Most important is DON'T change the slot after flashed because we already in the SAME Slot as the custom ROM.
       
###    5. I cannot install the Open GApps. It said 'Incompatible Devices Detected' and 'Updater process ended with ERROR: 64'
       Just restart the phone to system, let the system booting and then reboot back to twrp again, then install OG.
