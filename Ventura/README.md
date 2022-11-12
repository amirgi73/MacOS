Ventura (13.0) on X541uq
Bios Version: 311
Wifi+BT: Antel AC8260 - 8260NGW

This config has been updated to use OpenCore as Clover is dead.
udio Codec ALC294 : 
AppleAlc's layout-id=66 (Speakers + Mic + Headphone Jack (input + output)

Working:
CFG Lock disabled (Patched with uefi Shell) > CFG_Lock.md
Display Brightness (uses ACPI as WEG GPU Patches doesn't work here) > OP's `config.plist > DeviceProperties > PciRoot(0x0)/Pci(0x14,0x0) > acpi-wake-type | data| <01>`
GPU firmwarepatch (`AAPL,ig-platform-id=<00001B59>`, `force-online=<01000000>`)
CPU Powermanagement
Sleep
Keyboard
Touchpad in Pulling mode (Ghests are supported)
LAN
USB Ports
WebCam
App Store
Hardware Accelerated Video decoding
Battery status

Not Working/ Not tested:
Primary AR9565 Wifi Card > replaced by Intel AC8260 as I couldn't find any of natively supported Cards here in iran.
Brightness Keys
iMessage and Facetime
