# GPRW/UPRW/LANC Instant Wake Patch

Similar idea to the "Fixing Shutdown/Restart" section, macOS will instant wake if either USB or power states change while sleeping. To fix this we need to reroute the GPRW/UPRW/LANC calls to a new SSDT, verify you have instant wake issues before trying the below.

**Do not use all these ACPI patches at once**, look through your DSDT and see what you have:

| SSDT | ACPI Patch | Comments |
| :--- | :--- | :--- |
| [SSDT-GPRW](/extra-files/SSDT-GPRW.aml) | [GPRW to XPRW Patch](/extra-files/GPRW-Patch.plist) | Use this if you have `Method (GPRW, 2` in your ACPI |
| [SSDT-UPRW](/extra-files/SSDT-UPRW) | [UPRW to XPRW Patch](/extra-files/UPRW-Patch.plist) | Use this if you have `Method (UPRW, 2` in your ACPI |
| [SSDT-LANC](/extra-files/SSDT-LANC.aml) | [LANC to XPRW Patch](/extra-files/LANC-Patch.plist) | Use this if you have  `Device (LANC)` in your ACPI |

ACPI Patches and SSDTs courtesy of [Rehabman](https://www.tonymacx86.com/threads/guide-using-clover-to-hotpatch-acpi.200137/), 1Revenger1 and Fewtarius
