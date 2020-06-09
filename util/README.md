# Rom Splitter Utility
Included in this folder is a Windows excutable (Wine compatable) to split your assembled binary into two files for an emulator to read or to burn onto EEPROMs.
## Usage:

    stfbin2rom.exe
Opens the program and shows usage instructions.

    stfbin2rom.exe input
Takes file `input` and processes the file size accordingly, and creates an output of two files. Note, input without a specified directory assumes the output directory is the same as `stfbin2rom.exe`. This is useful if you want to drag and drop the binary onto the exe.

    stfbin2rom.exe input c:\output\directory

Takes `input` and processes the file size, then creates two output files in a specified directory. This is useful if you want to output directly to the m2emulator or MAME rom directory of `sfight` without having to copy/paste files.