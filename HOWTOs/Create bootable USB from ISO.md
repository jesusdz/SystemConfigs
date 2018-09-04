### How to create a bootable USB from an ISO file

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
