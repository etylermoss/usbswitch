# Vmswitch
A tool for attaching and detaching usb devices to / from, qemu / kvm virtual machines, written in bash.

# Usage 
```
vmswitch -adtADT [-lh]
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
DEVICE can be either the number, id, or name of the usb device. Run vmswitch with -l to see these values.
The -a -d and -t options cannot be run at the same time, likewise with -A -D and -T.
The program will need elevated privlages to run (WIP, may not be handled correctly).
```
# Dependencies
* lsusb [part of gnu coreutils]
* libvirt

[Untested on non qemu / kvm virtual machines]

