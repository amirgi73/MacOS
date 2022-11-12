# Ventura (13.0) on X541UQ

Bios Version: **311**
Wifi+BT: Intel AC8260 - 8260NGW

![Screenshot](Bildschirm foto 2022-11-13 um 01.59.50.png)

This config has been updated to use OpenCore as Clover is dead.

> There are 3 Config files in EFI Folder:
 - config.plist (finished config file)
 - config_debug.plist (same as finished but boot and OpenCore logs are enabled)
 - config_copy.plist (with **cfglock kernel patch** + Boot and OpenCore **logs** + **no USB port map** + no ACPI brightness) ideal for a usb_installer

## Guides:
[Dortania](https://dortania.github.io/getting-started/) for installing OpenCore as Well as almost all of required Hacks and Patches

## Working
 - **CFG Lock disabled** (Patched with UEFI shell) > check `CFG_Lock.md` file. (This is defferent for every Machine, don't use my values! Extract yours instead: [Guide](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html))
 - **Display Brightness**: (uses ACPI as WEG GPU Patches doesn't work here) > OP's `config.plist > DeviceProperties > Add > PciRoot(0x0)/Pci(0x14,0x0) > acpi-wake-type | data| <01>` 
 -  **GPU firamebuffer**: (`AAPL,ig-platform-id=<00001B59>`, `force-online=<01000000>`)(no need to spoof `device-id` or inject `EDID`)  
 -  **Audio**: Codec ALC294 :  AppleAlc's `layout-id=66` (Speakers + Mic + Headphone Jack (input + output)  
 -  **CPU Powermanagement**  
 -  **Sleep**  
 -  **Keyboard**  
 -  **Touchpad**: in Pulling mode (*unstable*)
 -  **LAN**  
 -  **USB Ports** 
 -  **WebCam** 
 -  **App Store** 
 -  **Hardware Accelerated Video decoding** 
 -  **Battery status**
 -  **NVRAM**

## Not Working/ Not tested

 - **Primary AR9565 Wifi Card** > replaced by Intel AC8260 as I couldn't find any of natively supported Cards here in iran. 
 - **Brightness Keys** 
 - **iMessage and Facetime**
 - **HDMI Output**

To Do:
1. Test touchpad in GPIO Mode
2. Fix Brightness Keys (fn+f3/f4)
3. Check HDMI Output and Fix if necessary
4. iMessage and Facetime
