CONFIG_BTUSB_AUTOSUSPEND = n
CONFIG_BTUSB_WAKEUP_HOST = y
CONFIG_BTCOEX = y

ifeq ($(CONFIG_BTUSB_AUTOSUSPEND), y)
	EXTRA_CFLAGS += -DCONFIG_BTUSB_AUTOSUSPEND
endif

ifeq ($(CONFIG_BTUSB_WAKEUP_HOST), y)
	EXTRA_CFLAGS += -DCONFIG_BTUSB_WAKEUP_HOST
endif

ifeq ($(CONFIG_BTCOEX), y)
	EXTRA_CFLAGS += -DCONFIG_BTCOEX
endif

EXTRA_CFLAGS += -Wno-unused-function

ifneq ($(KERNELRELEASE),)
	obj-m := rtk_btusb.o
	rtk_btusb-y = rtk_coex.o rtk_misc.o rtk_bt.o
else
	PWD := $(shell pwd)
	KVER := $(shell uname -r)
	KDIR := /lib/modules/$(KVER)/build

all:
	$(MAKE) -C ${KERNEL_SRC} M=${M} ARCH=${ARCH} CROSS_COMPILE=${CROSS_COMPILE} modules

clean:
	rm -rf *.o *.mod.c *.mod.o *.ko *.symvers *.order *.a

endif
