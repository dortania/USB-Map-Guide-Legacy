# Fixing USB Power

With Skylake and newer SMBIOS, Apple no longer provides USB power settings via IOUSBHostFamily, this means we need to adopt the same method real Macs do and supply macOS with a USBX device. This will set both the wake and sleep power values for all your USB ports. The following SMBIOS need USBX:

* iMac17,x and newer
* MacPro7,1 and newer
* MacMini8,1 and newer
* MacBook9,x  and newer
* MacBookAir8,x  and newer
* MacBookPro13,x and newer

Luckily you can use a precompiled file for USBX: [SSDT-USBX](https://github.com/khronokernel/USB-Map-Guide/blob/master/extra-files/SSDT-USBX.aml)
