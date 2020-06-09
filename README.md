
# stfdisasm
# Sonic the Fighters Disassembly
## A few notes:
It's in its infancy, and there are a few things that should be taken into consideration:

* There are two versions of the disassembly, rom_code1.asm and rom_code1(labels).asm. The first is a raw, buildable version of the game's ROM program with the GNU assembler and linker. The second contains all labels used in the IDA Pro database. The IDA database will most likely not be released due to the complexity and size. This second version is not buildable, please use rom_code1.asm.
* Why "rom_code1.asm"? The binary "rom_code1" is found as the main program file in both the files in Sonic Gems Collection and the Sonic the Fighters PSN/XBL release. As such, naming the file "rom_code1" makes it accurate to the original code.
* There may be errors, such as a labeled variables needing to be raw hex values instead. This cannot be fixed without experimentation, but for now, a bit perfect build is fine.
* The instructions to build the assembler and linker are in the GNU directory, along with the source code to binutils 2.16.1a, the last version of GNU's assembler to support the i960-COFF format.
* The binary once built will have 16 bytes of 00's at the end of the file. I don't know what causes this, but I assume it's something that happens once the linker links and removes all the symbols.
* The binary can be built with the following commands, adjust filenames to match your binutils build (Win/Linux) and what you name your files.
>	./i960-coff-as -AKB -J -o out.o rom_code1.asm

>	./i960-coff-ld -AKB --oformat binary -e 0xB0 -o rom.bin out.o
* The created binary will need to be split into a word-interleaved format in order to run on emulators or be burned to EPROMs. I will release a tool to do this soon.

I've spent probably close to two years on this now, and recently trying to reassemble the ROM helped fix a lot of things I wasn't aware of. I will try to get this repo 1:1 with the original ROM source, but I can't promise any time frame.
