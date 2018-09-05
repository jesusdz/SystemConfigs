# How to create a bootable USB from an ISO file

## Command

The following command copies all the contents of the ISO file into the specified device:

```
sudo dd if=filename.iso of=/dev/sdX bs=4M
sync
```

## Notes

* About the command
  * if: input file
  * of: output device (type a device without a partition number, e.g. sdd)
  * bs: I set it to 4M just to make it faster
* Make sure that boot from USB is enabled in the mother board.
* It the BIOS system does not recognize the USB, try with a different USB slot.
* It it keeps without recognizing it, maybe the pendrive is not supported by your mother board. Consider using another USB pendrive.

## For Windows 10 (and others) using WoeUSB

Looks like Windows 10 (and probably other versions) of windows are not dd-friendly.

I've managed to create a successful USB pendrive with windows with the WoeUSB tool.

To install WoeUSB in ArchLinux:

```
git clone https://aur.archlinux.org/woeusb-git.git
cd woeusb-git
makepkg
makepkg -i
```

Note that some dependencies will be required. Then, to use the tool:

```
sudo woeusbgui
```

And then, select the ISO image with the Window 10 OS, and the destination USB device.

## For Windows 10 (and others) from the command line

In theory, these steps should also do the trick to have a Windows 10 USB installer:

1. cfdisk (format the disk and create a gpt partition)
2. parted (to set the flag msftdata on this partition)
3. mkfs.fat (or vfat, to set the filesystem of this partition)
4. Mount the iso image and copy its contents into the usb (cp -R /media/iso/* /media/usb)

