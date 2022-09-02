# stfdisasm
# A Sonic the Fighters Disassembly
## Disassembly Notes:
This project is constantly maturing and there are a few things that should be taken into consideration:

* Why `rom_code1.asm`? The binary `rom_code1.bin` is found as the interleaved program ROM data in both the files in Sonic Gems Collection and the Sonic the Fighters PSN/XBL release. As such, naming the file`rom_code1` makes it accurate to the original distribution.
* You will see many instruction displacements with symbols/labels that have values added to them (such as `dword_8+1`). Some instructions require these symbols to assemble the instruction in the MEMB format rather than MEMA to achieve a bit-perfect assembly. A cleaner way to resolve instructions to MEMB when displacements are less than 4095 oct (or `0xFFF` hex) when required needs to be investigated.
* The instructions to build the assembler and linker are in the GNU directory, along with the source code to binutils 2.16.1a, the last version of GNU's assembler to support the i960-ELF format. (This will be replaced with a new repository eventually that will self-build i960-elf-gcc)
* Once the binary is assembled, it will have 16 bytes of `0x00` at the end of the file. I don't know what causes this, but I assume it's something that happens once the linker links and removes all the symbols.
* The binary can be built with the following commands, adjust filenames to match your binutils build (Win/Linux) and what you name your files.
`./i960-elf-as -AKB -J -o out.o rom_code1.asm`
`./i960-elf-ld -AKB --oformat binary -e 0xB0 -o rom.bin out.o`
* The created binary will need to be split into a word-interleaved format in order to run on emulators or be burned to EPROMs. The  `stfbin2rom.py` python script will allow you do do this easily.
* This has been nearly a four year running project of mine. The build is not 'shiftable' yet, but custom code can be inserted and referenced at the end of the ROM data in the `0xFF` filler.

## `stfbin2rom.py` - ROM Splitting Utility Usage:
    stfbin2rom.py [-h]
Opens the program and shows usage instructions.
`usage: stfbin2rom.py [-h] --input INPUT FILE [--output OUTPUT DIRECTORY]
                     [--verify | --no-verify]`

    stfbin2rom.py --input /path/to/rom.bin
Takes file `input` and processes the file size accordingly, and creates an output of two files. Note, input without a specified directory assumes the output directory is the same as `input`.

    stfbin2rom.py --input /path/to/rom.bin --ouput /different/path/than/input/

Takes `input` and processes the file size, then creates two output files in a specified directory. This is useful if you want to output directly to the m2emulator or MAME ROM directory of `sfight` without having to manually copy/paste files.

	stfbin2rom.py --input /path/to/rom.bin --verify
After the binary is successfully split, both files are compared to `sfight.md5` to have their checksum verified against known good files.
* `epr-19001.15` MD5: `744e46113217fc92c21ee9a4b16ed138`
* `epr-19002.16` MD5: `155bb4a50609a41e86f275fdba55211e`
