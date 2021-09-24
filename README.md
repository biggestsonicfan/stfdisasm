# stfdisasm
# Sonic the Fighters Disassembly
## A few notes:
This project is maturing and there are a few things that should be taken into consideration:

* Why `rom_code1.asm`? The binary `rom_code1.bin` is found as the main program file in both the files in Sonic Gems Collection and the Sonic the Fighters PSN/XBL release. As such, naming the file`rom_code1` makes it accurate to the original code.
* You will see many instruction displacements with symbols/labels that have values added to them (such as `dword_8+1`). Some instructions require these symbols to assemble the instruction in the MEMB format rather than MEMA to achieve a bit-perfect assembly. A cleaner way to resolve instructions to MEMB when displacements are less than 4095 oct (or `0xFFF` hex) when required needs to be investigated.
* The instructions to build the assembler and linker are in the GNU directory, along with the source code to binutils 2.16.1a, the last version of GNU's assembler to support the i960-COFF format.
* Once the binary is assembled, it will have 16 bytes of `0x00` at the end of the file. I don't know what causes this, but I assume it's something that happens once the linker links and removes all the symbols.
* The binary can be built with the following commands, adjust filenames to match your binutils build (Win/Linux) and what you name your files.
`./i960-coff-as -AKB -J -o out.o rom_code1.asm`
`./i960-coff-ld -AKB --oformat binary -e 0xB0 -o rom.bin out.o`

* The created binary will need to be split into a word-interleaved format in order to run on emulators or be burned to EPROMs. The tool to do this is in the `util` folder.

This has been nearly a three year running project of mine. The build is not 'shiftable' yet, but custom code can be inserted and referenced at the end of the ROM data in the `0xFF` filler.