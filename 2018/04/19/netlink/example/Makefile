# Example run in CentOS 7.4 with kernel 3.10.0-693.el7.x86_64
# Tabs maybe transfer to space, this should be check or correct after copy.

CONFIG_MODULE_SIG=n
obj-m += kernel/netlink_instance.o
nl_kern-objs := kernel/netlink_instance.o

all: kernel-build kernel-clean-temporary user-build
	@tput setaf 3
	@echo "    done: all"
	@tput sgr0
clean: kernel-clean user-clean
	@tput setaf 3
	@echo "    done: clean"
	@tput sgr0



kernel-build:
	@tput setaf 1
	@echo "    kernel-build"
	@tput sgr0
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
kernel-clean:
	@tput setaf 1
	@echo "    kernel-clean"
	@tput sgr0
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
kernel-clean-temporary:
	@tput setaf 1
	@echo "    kernel-clean-temporary"
	@tput sgr0
	-rm -rf *.o *~ core .depend .*.cmd *.mod.c .tmp_versions
	-rm -rf kernel/*.o kernel/*~ kernel/core kernel/.depend kernel/.*.cmd  kernel/*.mod.c kernel/.tmp_versions
	-rm -rf Module.symvers modules.order
kernel-module-install:
	@tput setaf 1
	@echo "    kernel-module-install"
	@tput sgr0
	-sudo insmod netlink-instance.ko
kernel-module-uninstall:
	@tput setaf 1
	@echo "    kernel-module-uninstall"
	@tput sgr0
	-sudo rmmod netlink-instance
kernel-clean-ring-buffer:
	@tput setaf 1
	@echo "    kernel-clean-ring-buffer"
	@tput sgr0
	sudo dmesg -c > /dev/null



user-build:
	@tput setaf 1
	@echo "    user-build"
	@tput sgr0
	gcc user/user_netlink.c -o genl_user
user-clean:
	@tput setaf 1
	@echo "    user-clean"
	@tput sgr0
	rm -rf *.out genl_user

