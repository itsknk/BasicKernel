# BasicKernel
A very simple Kernel written in C that displays a string and then hangs.

## Installation
Have to install gcc, nasm, grub, and qemu(optional).

## Building the Kernel
1. Download the repo and cd into it.
2. First Build the assembly file with command ```nasm -f elf32 kernel.asm -o kernasm.o```.
3. Next Build the C file with command ```gcc -m32 -c kernel.c -o kerc.o```.
4. Now link both the kernasm file and kerc file with command ```ld -m elf_i386 -T link.ld -o kernel kernasm.o kerc.o```.

## Usage
There are two ways to run the Kernel.
1. This is the direct way, first rename the kernel file as kernel--001(001 meaning the version number, can be anything). Copy this kernel--001 file to the /boot directory. Open the grub.cfg inside grub folder and add the entry: 
```
 menuentry 'My Kernel' {
    set root='hd0,5'
    multiboot /boot/kernel-001 ro
}
```
Here hd0,5 is sda/sda5, set accordingly. Then reboot.

2. If you've installed qemu then you can run this in the virtual machine using the command: `qemu-system-i386 -kernel kernel-001`. 

## License
[MIT](https://github.com/itsknk/basicKernel/blob/master/LICENSE)