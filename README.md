# stfdisasm
# Sonic the Fighters Disassembly
## A few notes:
It's in its infancy, and there are a few things that should be taken into consideration:

* There are two versions of the disassembly, rom_code1.asm and rom_code1(labels).asm. The first is a raw, buildable version of the game's ROM program with the GNU assembler and linker. The second contains all labels used in the IDA Pro database. The IDA database will most likely not be released due to the complexity and size. This second version is not buildable, please use rom_code1.asm.
* Why "rom_code1.asm"? The binary "rom_code1" is found as the main program file in both the files in Sonic Gems Collection and the Sonic the Fighters PSN/XBL release. As such, naming the file "rom_code1" makes it accurate to the original code.
* There may be errors, such as a labeled variables needing to be raw hex values instead. This cannot be fixed without experimentation, but for now, a bit perfect build is fine.
* The instructions to build the assembler and linker are in the GNU directory, along with the source code to binutils 2.16.1a, the last version of GNU's assembler to support the i960-COFF format.

I've spent probably close to two years on this now, and recently trying to reassemble the ROM helped fix a lot of things I wasn't aware of. I will try to get this repo 1:1 with the original ROM source, but I can't promise any time frame.
