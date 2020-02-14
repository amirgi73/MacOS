
# MacOS
A repo containing Files, kests, etc for installing OSx on  Asus X542UQ.
Note that this is a personal Repo for myself to remember how to install back OSx on my Laptop at the future.

## Hardware:
- Asus X542UQ
- BIOS Version: 309
- Intel Core-i5 7200u (Kabylake)
- 8GB RAM
- Intel HD 620 Gpu + Nvidia 940mx (nvidia will be disabled using config.plist file as OSx doesn't support it)
- Atheros AR9565 WIFI
- Elan1200 Touchpad
- ALC294 Audio Codec

## Clover

Use **Rehabman's Clover fork** as with official clover some kexts and patches do not work.

## Installer
Create the installer using this guide:
https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/
Do not forgot the `VoodooTSCSync.kext`. Without it the installer may stuck at boot or hang during the installation.


## Audio
https://www.tonymacx86.com/threads/an-idiots-guide-to-lilu-and-its-plug-ins.260063/

Use **AppleAlc Kext** with a code generated from [Hackingtool](https://www.tonymacx86.com/threads/an-idiots-guide-to-lilu-and-its-plug-ins.260063/#Hacktool) for `Layout ID 12`(`Spoof Audio Device ID` in Hackingtool should be unchecked). Place the code from Hackingtool to the Devices > Properties in the `config.plist` file from clover. Note that in the `config.plist` file Devices > Audio there should be a key named `Inject` with a **string** value = `NO`.
(with audio layout 12 the audio jack and Speakers function normally, although the microphone doesn't work, and the HDMI audio is not tested.)
The laptop uses `Alc294` Codec.

## Graphics
You need `VoodooTSCSync.kext`, `Lilu.kext` and `WhateverGreen.kext`. Without VoodooTSCSync.kext you wouldn't be able to boot or get very annoying graphic distortions.

## DSDT Patches:
guide for patching DSDT:
https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/

Apply this patches:
 - [bat] Asus N55Sl/Vivobook
 - [syn] Fix PARSEOP_ZERO Error (agressive)
 - [igpu] Brightness fix
 - [sys] Fix_WAK Arg0 V2
 - [sys] Fix Mutex with non-zero SyncLevel
 - [sys] HEPT fix
 - [sys] IRQ fix
 - [sys] RTC fix
 - [sys] OS check fix windows 10
 - [sys] Shutdown fix V2
 - [sys] SMBUS fix
 - Add asus repository and patch for fn keyboard keys according to this guide: https://github.com/hieplpvip/AsusSMC

***[NOTE]*** The Patched `DSDT.dsl` file is provided in this repo and is for my own personal use. Every System will have different DSDT and SSDTs and my file **probably never works on any other system**, even if you have the exact model and Hardware as me. Use the linked guide above to learn how to patch your own DSDT and SSDTs.

***[NOTE]*** The patches in Asus Repository dosn't work. for fixing Brightness keys use this patch INSTED:
(more informations here [on section: Brightness Keys]: https://www.tonymacx86.com/threads/guide-patching-dsdt-ssdt-for-laptop-backlight-control.152659/)

    into method label _Q0E replace_content
    begin
    // Brightness Down\n
        Notify(\_SB.PCI0.LPCB.PS2K, 0x0405)\n
    end;
    into method label _Q0F replace_content
    begin
    // Brightness Up\n
        Notify(\_SB.PCI0.LPCB.PS2K, 0x0406)\n
    end;

    
    
## Touchpad
Due to Asus' buggy implementations of GPIO, touchpad in GPIO mode whould lag and is not usable (at least with the current BIOS version: 309) so you have to use **Pulling Mode** which does not need any DSDT patches. Just install the `VoodooI2C.kext` and `VoodooI2CHID.kext` in `Library/Extension`.
IF you want to test the Interrupt Mode > use the ACPI name `ETPD` and GPIO pin hex: `0x34` (this is for my own reference only. for your system the pin number and even ACPI name may be different. Check [VoodooI2C wiki](https://voodooi2c.github.io/#Installation/Installation) for guides on how to use Interrupt Mode and finding your system's GPIO pin number and hex.)

## Wifi
AR9565 is not supported in Mojave. Currently the only way is to **replace the native IO80211Family.kext with the patched one** provided in the Wifi folder in this repo. backup the original kext from /S/L/E (simply use cp -R command to copy it somewhere else)

    cp -R /System/Library/Extensions/IO80211Family.kext ~/Desktop/

then remove the IO80211Family.kext from /S/L/E

    sudo rm -Rf /System/Library/Extensions/IO80211Family.kext

and install the patched one in /S/L/E with the Kextbeast tool. Now install `ATH9KInjector.kext` and `ATH9Fixup.kext` using Hackingtool. (Hackingtool will repair permissions and will regenerate kext cache). Finally you need to add  `-ath9565` as boot aurgument to clover.

## Acknowledgments:
Please note that non of this tools and kexts are from me. I'm just a guy who tested them and collected them here for my personal future reference.
 - **Rehabman** for his great work and providing most of the tools and Kexts used to install OSx on not Apple Hardware.
- https://tonymacx86.com for providing the guides, tools and support to successfully install OSx.
- Other developers that their tools used and mentioned here.







