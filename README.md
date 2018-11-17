# A minimalist Linux .config file for Dell XPS 15 (9560)

This is a minimalist linux kernel .config file for the Dell XPS 15 (2017 edition); minimalist meaning that if certain hardware is not present on the device, the kernel option must be OFF (=n). If that is not so, please file a bug.

The configuration has three Gentoo-specific kernel options, but that should not prevent you from using it with Vanilla kernel sources. It has EFI support compiled in, so once the kernel is built, you should be able to normally place it onto your EFI partition and have it working.

When building a .config file, you always have to make some tradeoffs. Because this is a laptop, I am following these (in descending order of importance):

 * Power saving and battery longevity,
 * performance (raw computational power & benchmarks),
 * lattency and jitter (last, only somewhat important).
 
## What works

 * USB-C port completely works,
 * PCI-E SD card reader,
 * reliable suspend,
 * touchpad with SMbus support,
 * touchscreen,
 * EFI boot.
 
## What is not included
 
Some features are left out, notably:
 
 * Swap support,
 * Bluetooth support,
 * module support (required by proprietary Nvidia drivers).

## Current known problems

 * To make sound working, you have to suspend the device and wake it up again. Most probably a kernel bug.
 * Unused nVidia card draws significant amount of power. Run `sudo sh -c 'echo auto > /sys/bus/pci/devices/0000\:01\:00.0/power/control'` once booted to prevent that. Having your own SystemD boot service to do that is a fine solution.

