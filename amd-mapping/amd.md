# USB Mapping

So with the prerequisites out of the way, we can finally get to the meat of this guide. And now we get to finally read one of my favorite book before I go to bed each night: [The Advanced Configuration and Power Interface (ACPI) Specification!](https://uefi.org/sites/default/files/resources/ACPI_6_3_final_Jan30.pdf) 

Now if you haven't read through this before(which I highly recommend you do, it's a thrilling tale), I'll point you to the meat of the USB situation:

* Section 9.14: _UPC (USB Port Capabilities)

Here we're greeted with all the possible USB ports in ACPI:

| Type | Info | Comments |
| :--- | :--- | :--- |
| 0 | USB 2.0 Type-A connector | This is what macOS will default all ports to when no map is present |
| 3 | USB 3.0 Type-A connector | 3.0, 3.1 and 3.2 ports share the same Type |
| 8 | Type C connector - USB 2.0-only | Mainly seen in phones
| 9 | Type C connector - USB 2.0 and USB 3.0 with Switch | Flipping the device **does not** change the ACPI port |
| 10 | Type C connector - USB 2.0 and USB 3.0 without Switch | Flipping the device **does** change the ACPI port. generally seen on 3.1/2 motherboard headers |
| 255 | Proprietary connector | For Internal USB ports like Bluetooth |

## AMD and 3rd Party USB Mapping

To be written, for now see the  [AMD-USB-map.md](https://github.com/dortania/OpenCore-Desktop-Guide/blob/master/AMD/AMD-USB-map.md) for the time being.

For all I care, AMD hackintoshes don't exist. Please don't make me look at another AMD DSDT please, just buy Intel

To do:

* Getting your DSDT
* Creating the map
* Port mapping on screwed up DSDTs
* Port mapping when you have multiple of the same controller

#### Cry a bit

#### Cry some more

#### Buy some Intel hardware