
obj-m += mymodule.o 
# This line tells 'obj-m += mymodule.o' the kernel build system that
# we want to build a module (indicated by the obj-m) named mymodule.o. 
# The .o file will be created from a corresponding mymodule.c source file.

all:
# "-C /lib/modules/$(shell uname -r)/build"Changes to the kernel build directory for the current running kernel.
# the "-C" option changes to a specific directory before to execute the make file, therefore there is a makefile in /lib/modules/$(shell uname -r)/build
# M=$(PWD): Tells the kernel build system that the module source is in the current directory.
# modules: Instructs to build the modules specified by obj-m.3
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules 

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean