# Makefile for custom kernel

# Architecture flags (doesn't change the architecture set
# inside the assembly file).
#ARCH=i386
#ARCH_FLAGS=-march=$(ARCH) -m32

# General flags for tools.
#CC_FLAGS=$(ARCH_FLAGS) -O0 -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include/ -I./vfs/ -c
#LD_FLAGS=-m elf_$(ARCH)

kernel: force_perform
	# Assemble the entry point
	echo Assembling start.asm...
	nasm -f elf64 -o start.o start.asm

	# Compiling gcc
	gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o main.o main.c
	gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o screen.o screen.c

	# Linking the kernel
	echo Linking kernel...
	ld -T link.ld -o kernel.bin start.o main.o screen.o

clean: 
	rm *.o 

force_perform:
	true