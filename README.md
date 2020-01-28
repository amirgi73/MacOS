# MacOS
A repo containing Files, kests, etc for installing OSx on  Asus X542UQ

# Clover
use Rehabman's Clover fork as with official clover some kexts and patches do not work.

# Installer
create the installer using this guide:
https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/
do not forgot the VoodooTSCSync.kext without it the installer may stuck at boot or hang during the installation.


# Audio
https://www.tonymacx86.com/threads/an-idiots-guide-to-lilu-and-its-plug-ins.260063/

Use AppleAlc Kext with a code generated from Hackingtool for Layout ID 12. Place the code from Hckingtool to the Devices > Properties in the config.plist file from clover. Note that in the config.plist file Devices > Audio there should be a key named Inject with a string value = NO.
(with audio layout 12 the audio jack and Speakers function normally, although the microphone dosn't work, and the HDMI audio is not tested.)
The laptop uses Alc254 Codec.

# Graphics
You need VoodooTSCSync kext and Lilu and WhateverGreen. Without VoodooTSCSync kext you whouldnt be able to boot or get very annoting graphic distortions.

# DSDT Patches:
guide for patching DSDT:
https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/

apply this patches:
[bat] Asus N55Sl/Vivobook
[syn] Fix PARSEOP_ZERO Error (agressive)
[igpu] Brightness fix
[sys] Fix_WAK Arg0 V2
[sys] Fix Mutex with non-zero SyncLevel
[sys] HEPT fix
[sys] IRQ fix
[sys] RTC fix
[sys] OS check fix windows 10
[sys] Shutdown fix V2
[sys] SMBUS fix

add asus repository and patch for fn keyboard keys according to this guide:
https://github.com/hieplpvip/AsusSMC

# Touchpad
due to Asus' buggy implementations of GPIO, touchpad in GPIO mode whould lag and is not usable (at least with the current BIOS version: ) so you have to use interrupt mode with does not need any DSDT patches. Just install the VoodooI2C and VoodooI2CHID kexts in L/E

# Wifi
AR9565 is not supported in Mojave. currently the noly way is to replace the native IO80211Family.kext with the patched one provided in the Wifi folder. Remove the original IO80211Family.kext from /S/L/E then install the patched one in /S/L/E with the Kextbeast tool. then install ATH9KInjector.kext and ATH9Fixup.kext with the Hackingtool (Hakingtool will repair permissions and will regenerate kext cache). then you need to add -ath9565 as boot aurgument to clover.





