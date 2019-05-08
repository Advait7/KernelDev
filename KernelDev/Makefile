# Makefile for custom kernel

kernel: force_perform
	# Assemble the entry point
	echo Assembling start.asm...
	nasm -f elf64 -o start.o start.asm

	# Linking the kernel
	echo Linking kernel...
	ld -T link.ld -o kernel.bin start.o

clean: 
	rm *.o 

force_perform:
	true