# SPDX-License-Identifier: GPL-2.0-only

# Global compilation flags
ccflags-y += -DCONFIG_RTW88_DEBUG=1
ccflags-y += -DCONFIG_RTW88_DEBUGFS=1
ccflags-y += -DCONFIG_RTW88_LEDS=1

# Core driver logic
obj-$(CONFIG_RTW88_CORE) += rtw88_core.o
rtw88_core-y := main.o mac80211.o util.o debug.o tx.o rx.o mac.o \
                 phy.o coex.o efuse.o fw.o ps.o sec.o bf.o regd.o \
                 sar.o led.o

# WoWLAN (Wake on WLAN) support
rtw88_core-$(CONFIG_PM) += wow.o

# USB transport support
obj-$(CONFIG_RTW88_USB) += rtw88_usb.o
rtw88_usb-y := usb.o

# 8812A specific code
# Added rtw88xxa.o to fix undefined symbols
obj-$(CONFIG_RTW88_8812A) += rtw88_8812a.o
rtw88_8812a-y := rtw8812a.o rtw8812a_table.o rtw88xxa.o

# 8812AU driver module
obj-$(CONFIG_RTW88_8812AU) += rtw88_8812au.o
rtw88_8812au-y := rtw8812au.o

# 8821A specific code
# Added rtw88xxa.o here as well for consistency
obj-$(CONFIG_RTW88_8821A) += rtw88_8821a.o
rtw88_8821a-y := rtw8821a.o rtw8821a_table.o rtw88xxa.o

# 8821AU driver module
obj-$(CONFIG_RTW88_8821AU) += rtw88_8821au.o
rtw88_8821au-y := rtw8821au.o
