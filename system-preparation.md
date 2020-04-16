# System Preparation

So before we can USB map, we need to set a couple things:

* [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/) under both EFI/OC/Kexts and config.plist -> Kernel -> Add
   * We need this kext to make sure any ports not defined in ACPI will still show up in macOS, note that this *shouldn't* be required on Skylake and newer as the USB ports are defined within ACPI
   * Note that this **does not work on AMD**
* config.plist -> Kernel -> Quirks -> XhciPortLimit -> True
   * So we can temporally get around the 15 port limit to map our ports
* config.plist -> ACPI -> Patch -> EHCI and XHCI ACPI renames

The reason we need these ACPI renames are due to conflicting with Apple's own USB map, fun fact even Apple has to USB map as well! You can actually find Apple's USB map within IOUSBHostFamily.kext -> PlugIns -> AppleUSBHostPlatformProperties.kext, though newer Macs actually port map with their ACPI tables instead. 

SMBIOSes that do not need the ACPI renames:

* iMac18,x and newer
* MacPro7,1 and newer
* MacMini8,1 and newer
* MacBook9,x  and newer
* MacBookAir8,x  and newer
* MacBookPro13,x and newer

And so with older SMBIOSes(one's not listed above), we need to make sure their port map does not attach while we're trying to USB map ourselves. Else some ports may disappear, and please check you do have these ports in your ACPI tables **before** applying these patches as we don't want to patch the wrong devices. If you do find your USB controller needs renaming, write down their original names before the rename as this will make USB mapping down the road a bit easier:

* **XHC1 to SHCI**: Needed for Skylake and older SMBIOS

| Key | Type | Value |
| :--- | :--- | :--- |
| Comment | String | XHC1 to SHCI |
| Count | Number | <0> |
| Enabled | Boolean | YES |
| Find | Data | <58484331> |
| Limit | Number | <0> |
| Replace | Data | <53484349> |
| Skip | Number | <0> |
| Tablelength | Number | <0> |
| TableSignature | Data | <> |

* **EHC1 to EH01**: Needed for Broadwell and older SMBIOS

| Key | Type | Value |
| :--- | :--- | :--- |
| Comment | String | EHC1 to EH01 |
| Count | Number | <0> |
| Enabled | Boolean | YES |
| Find | Data | <45484331> |
| Limit | Number | <0> |
| Replace | Data | <45483031> |
| Skip | Number | <0> |
| Tablelength | Number | <0> |
| TableSignature | Data | <> |

* **EHC2 to EH02**: Needed for Broadwell and older SMBIOS

| Key | Type | Value |
| :--- | :--- | :--- |
| Comment | String | EHC2 to EH01 |
| Count | Number | <0> |
| Enabled | Boolean | YES |
| Find | Data | <45484332> |
| Limit | Number | <0> |
| Replace | Data | <45483032> |
| Skip | Number | <0> |
| Tablelength | Number | <0> |
| TableSignature | Data | <> |

And for those worried about ACPI patches applying to other OSes, these will only be temporary and will be removed once we've mapped our ports.

# Parting ways

But now we must part into 2 sections, depending on which hardware you have:

* [Intel USB Mapping](/intel-mapping/intel.md)
* [AMD and 3rd Party USB Mapping](/amd-mapping/amd.md)