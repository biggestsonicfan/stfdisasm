
# stfdisasm
# Sonic the Fighters Disassembly
## A few notes:
It's in its infancy, and there are a few things that should be taken into consideration:

* Why "rom_code1.asm"? The binary "rom_code1" is found as the main program file in both the files in Sonic Gems Collection and the Sonic the Fighters PSN/XBL release. As such, naming the file "rom_code1" makes it accurate to the original code.
* There may be errors, such as a labeled variables needing to be raw hex values instead. This cannot be fixed without experimentation, but for now, a bit perfect build is fine.
* The instructions to build the assembler and linker are in the GNU directory, along with the source code to binutils 2.16.1a, the last version of GNU's assembler to support the i960-COFF format.
* The binary once built will have 16 bytes of 00's at the end of the file. I don't know what causes this, but I assume it's something that happens once the linker links and removes all the symbols.
* The binary can be built with the following commands, adjust filenames to match your binutils build (Win/Linux) and what you name your files.
>	./i960-coff-as -AKB -J -o out.o rom_code1.asm

>	./i960-coff-ld -AKB --oformat binary -e 0xB0 -o rom.bin out.o
* The created binary will need to be split into a word-interleaved format in order to run on emulators or be burned to EPROMs. I will release a tool to do this soon.

This has been nearly a three year running project of mine. The build is not 'shiftable' yet, but custom code can be inserted and referenced at the end of the ROM data in the `0xFF` filler.