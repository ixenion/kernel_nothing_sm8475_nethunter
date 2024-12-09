Nethunter ready kernel source for Nothing Phone 2.

For kernel source compilation use:
```shell
bash build.sh
```

Or check release page for kernel .zip.

Also you need to install additional vendor firmware.
If dont - you wont be able to do
```shell
sudo ifconfig wlan1 up
```
And got error:
```
$ dmesg | grep "rt2"

[17182.790853] [T22200] ieee80211 phy4: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[17182.875815] [T22200] ieee80211 phy4: rt2x00_set_rf: Info - RF chipset 0005 detected
[17527.234002] [T15235] ieee80211 phy4: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[17527.234034] [T15235] rt2800usb 2-1:1.0: Direct firmware load for rt2870.bin failed with error -2
[17527.234040] [T15235] rt2800usb 2-1:1.0: Falling back to sysfs fallback for: rt2870.bin
[17527.240358] [T15236] ueventd: firmware: loading 'rt2870.bin' for '/devices/platform/soc/a600000.ssusb/a600000.dwc3/xhci-hcd.1.auto/usb2/2-1/2-1:1.0/firmware/rt2870.bin'
[17527.243813] [T15236] ueventd: firmware: could not find firmware for rt2870.bin
[17527.243838] [T15236] ueventd: firmware: attempted /etc/firmware/rt2870.bin, open failed: No such file or directory
[17527.243851] [T15236] ueventd: firmware: attempted /odm/firmware/rt2870.bin, open failed: No such file or directory
[17527.243860] [T15236] ueventd: firmware: attempted /vendor/firmware/rt2870.bin, open failed: No such file or directory
[17527.243870] [T15236] ueventd: firmware: attempted /firmware/image/rt2870.bin, open failed: No such file or directory
[17527.243881] [T15236] ueventd: firmware: attempted /vendor/firmware_mnt/image/rt2870.bin, open failed: No such file or directory
[17527.244054] [T15236] ueventd: loading /devices/platform/soc/a600000.ssusb/a600000.dwc3/xhci-hcd.1.auto/usb2/2-1/2-1:1.0/firmware/rt2870.bin took 5ms
[17527.244782] [T15235] ieee80211 phy4: rt2x00lib_request_firmware: Error - Failed to request Firmware
```

Firmware (installed through Magisk)
https://github.com/rithvikvibhu/nh-magisk-wifi-firmware
