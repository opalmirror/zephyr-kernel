ccflags-y += -I$(srctree)/include/drivers
ccflags-y += -I$(srctree)/drivers
asflags-y := ${ccflags-y}

obj-y += board.o
obj-$(CONFIG_PINMUX) += galileo_pinmux.o
obj-$(CONFIG_REBOOT) += galileo_reboot.o
