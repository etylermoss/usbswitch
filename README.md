# Usbswitch
A tool for attaching and detaching usb devices to / from, qemu / kvm virtual machines, written in bash.

# Usage 
```
usbswitch -adtADT [-lh]
Options:
	-l,       List usb devices with their number, id, and name
	-a DEVICE DOMAIN,	Attach the device to the VM
	-d DEVICE DOMAIN,	Detach the device from the VM
	-t DEVICE DOMAIN,	Toggle devices attachment to the VM
	-A DEVICE DOMAIN,	Add the device to the VM config
	-D DEVICE DOMAIN,	Remove the device from the VM config
	-T DEVICE DOMAIN,	Toggle the device's presence in the VM config
	-h,			Display usage information
  
Notes:
DEVICE can be either the number, id, or name of the usb device. Run usbswitch with -l to see these values
The -a -d and -t options cannot be run at the same time, likewise with -A -D and -T
The program will need elevated privlages to run (WIP, may not be handled correctly)

Examples:

	$ usbswitch -l
	Number	ID	Name
	1	1b09	Corsair K70R Keyboard
	2	0037	Razer DeathAdder
	3	0001	Cambridge Silicon Bluetooth Dongle
	
	$ usbswitch -a 1 win10
	Attaching:
	1	1b09	Corsair K70R Keyboard
	
	$ usbswitch -A Razer win10
	Adding to domain config:
	2	0037	Razer DeathAdder
	
	$ usbswitch -d 0037 win10
	Detaching:
	2	0037	Razer Death
	
```
# Dependencies
* lsusb
* libvirt

# Bugs
* Currently does not support searching by names using multiple words. E.g: '$ usbswitch -a Razer DeathAdder', instead search for just 'Razer', or use the ID and Number values.
* Due to the way it uses usb id's, it cannot attach devices where there is multiple of the same device plugged in.
* Unable to parse more than 2 arguments at the same time, except with -l.

[Untested on non qemu / kvm virtual machines]

