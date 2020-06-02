# stfdisasm
# Sonic the Fighters Disassembly
## A few notes:
It's in it's infancy, and there are a few things that should be taken into consideration:

    This build is not close to being build-able. Once I am able to compile a valid Model2b binary, I can then begin comparing the binary to the source ROM and made changes accordingly.
    To reduce the size of the disassembly, the memory segment of the IDA file has been stripped, however the labels remain. This is why you will see some labels with no references. Bare with me until I figure out a solution for this.
    There are errors. Probably lots of them. Things like loc_FFF8+7 should be 0xFFFF, I just haven't fixed them all yet.
    I am new to assembly, and do not fully comprehend how to use include or macros yet.
    HELP WANTED! I don't know what people can do, submit issues for what you find or even pull requests would be nice though to fix things. Keep in mind I have to make the changes in IDA Pro first, then re-export to an ASM file, so any submitted issues or pull requests will take time to fix.

I've spent probably close to two years on this now, and recently trying to reassemble the ROM helped fix a lot of things I wasn't aware of. I will try to get this repo 1:1 with the original ROM source, but I can't promise any time frame.
