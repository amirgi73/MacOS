
# Sonoma (14.2.1) on X541UQ

Bios Version: **311**

![Screenshot](https://github.com/amirgi73/MacOS/blob/master/Sonoma/Bildschirmfoto%202023-12-31%20um%2003.41.34.png)

This config uses OpenCore 0.9.7
This config uses `MacBookPro15,2` as Platform-ID while the Previous MacBookPro14,1 isn't supported in Sonoma.

### EFI.zip Direct Download Link:
`https://github.com/amirgi73/MacOS/raw/master/Sonoma/EFI.zip`
## Guides:
[Dortania](https://dortania.github.io/getting-started/) for installing OpenCore as Well as almost all of required Hacks and Patches

## Working
 - [x] **CFG Lock disabled** (Patched with UEFI shell) > check `CFG_Lock.md` file. (This is defferent for every Machine, don't use my values! Extract yours instead: [Guide](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html))
 - [x] **Display Brightness**: (uses ACPI as WEG GPU Patches doesn't work here) > OP's `config.plist > DeviceProperties > Add > PciRoot(0x0)/Pci(0x14,0x0) > acpi-wake-type | data| <01>` 
 -  [x] **GPU firamebuffer**: (`AAPL,ig-platform-id=<00001B59>`, `force-online=<01000000>`)(no need to spoof `device-id` or inject `EDID`)  
 -  [x] **Audio**: Codec ALC294 :  AppleAlc's `layout-id=66` (Speakers + Mic + Headphone Jack (input + output + HDMI Audio)  
 -  [x] **CPU Powermanagement**  
 -  [x] **Sleep**  
 -  [x] **Keyboard**  
 -  [ ] **Touchpad**: in Pulling mode (*unstable*)
 Model: Elan1200, GPIO PIN: `0x55`, due to Asus's buggy implementation of GPIO it *won't work* in Interrupt mode. GPIO Patches are included in `SSDT-GPI0.aml`. They won't work however. 
 -  [x] **LAN**  
 -  [x] **USB Ports** 
 -  [x] **WebCam** 
 -  [x] **App Store** 
 -  [x] **Hardware Accelerated Video decoding** 
 -  [x] **Battery status**
 -  [x] **NVRAM**
 -  [x] **Brightness Keys** (fn+f5/f6)
 -  [x] **HDMI Output** (video + audio)
 -  [x] **iMessage and Facetime**

## Not Working/ Not tested

 - **Primary AR9565 Wifi Card**


