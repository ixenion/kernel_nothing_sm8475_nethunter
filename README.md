Nethunter ready kernel source for Nothing Phone 2.

1. Install build dependencies:
```shell
sudo apt install make gcc zlib1g zlib1g-dev libssl-dev flex bison build-essential libncurses-dev zstd cpio zip
```

2. Make shure python is available by `python --version`. If not:
```shell
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 1
```

3. For kernel source compilation use:
```shell
bash build.sh
```
(Or check release page for kernel .zip.)

4. On building choose (for magisk)
```
Include KernelSU? If unsure, say N. (Y/N) N
Do you want to do a clean build? If unsure, say N. (Y/N) Y
Do you want to modify .config? If unsure, say N. (Y/N) Y

!!! Important: load nethunter ready config:
Choose <load> and enter build_configs/v1.0.0/config
this config contains basic nethunter setups and drivers for:

    Mediatek:
    - MT7601U (USB)
    - MT76x0U (USB)
    - MT76x0E (PCIe)
    - MT76x2E (PCIe)
    - MT76x2U (USB)
    - MT7603E (PCIe)
    - MT7615E and MT7663E (PCIe)
    - MT7663U (USB)
    - MT7663S (SDIO)
    - MT7915E (PCIe)
    
    Ralink:
    - rt2500 (USB)
    - rt2501/rt73 (USB)
    - rt27xx/rt28xx/rt30xx (USB)
    - rt33xx devices
    - rt35xx devices
    - rt3573 devices
    - rt53xx devices
    - rt55xx devices
    
    Realtek:
    - RTL8192CE/RTL8188CE
    - RTL8192SE/RTL8191SE PCIe
    - RTL8192DE/RTL8188DE PCIe
    - RTL8723AE PCIe
    - RTL8723BE PCIe
    - RTL8188EE
    - RTL8192EE
    - RTL8821AE/RTL8812AE
    - RTL8192CU/RTL8188CU USB
    
    SDR:
    - AirSpy
    - HackRF
    - Mirics MSi2500
    - Digital TV support
    - Software defined radio support


Enable vDSO for 32-bit applications (COMPAT_VDSO) [Y/n/?] (NEW) Y
Compile the 32-bit vDSO for Thumb-2 mode (THUMB2_COMPAT_VDSO) [Y/n/?] (NEW) Y

Link Time Optimization (LTO)
> 1. None (LTO_NONE)
  2. Clang Full LTO (EXPERIMENTAL) (LTO_CLANG_FULL) (NEW)
  3. Clang ThinLTO (EXPERIMENTAL) (LTO_CLANG_THIN) (NEW)
choice[1-3?]: 3

Use Clang's Control Flow Integrity (CFI) (CFI_CLANG) [N/y/?] (NEW) N
Use RELR relocation packing (RELR) [Y/n/?] (NEW) Y
```






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
