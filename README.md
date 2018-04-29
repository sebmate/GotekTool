# GotekTool
Linux Bash script to mass-copy files to USB sticks that had been formatted for Gotek USB floppy drive emulators.

The Gotek USB floppy disk drive emulators are excellent products. They allow you to upgrade old floppy-based hardware with USB storage capabilities. Unfortunately, the available (Windows only) software is a bit awkward to use, because you have to first copy your files manually into directories and then sync all directories with the USB stick. It is also difficult to estimate how much data can fit onto one virtual floppy, therefore your are very likely to waste space.

This Linux script copies files to USB sticks formatted for the Gotek drive. It automatically switches to the next floppy disk when one is full. Several options are available for handling directories (see below). After uploading data to an USB stick, an index text file is created so that you can find the files quickly later on.

I programmed this script to make large amounts of style files available on my Yamaha PSR-8000 keyboard, which I had upgraded with a Gotek SFR1M44-U100K. It makes the provision of files via a USB stick a breeze!

Attention: The script must be properly configured before use (mounting point and device must be changed if necessary). Use at your own risk!!


    GotekTool - A Batch File Copier for Gotek USB Floppy Disk Emulators
    Copyright 2017 Sebastian Mate

               Usage: gotektool SOURCEDIRECTORY STARTFLOPPY MODE

     SOURCEDIRECTORY: The base directory to be copied.
         STARTFLOPPY: The number of the first virtual floppy.
                MODE: The mode of file handling, which is:
                      1 = Flatten directories and copy all files to the root directory of the virtual floppies.
                      2 = As 1, but also change floppy for each directory.
                      3 = Preserve original directory structures.
                      4 = Move contents from root directories to separate virtual floppies.

          WARNING: This tool does erase data on the target device and is potentially dangerous.
                   Use on your own risk!

## Examples
- Mode 1: Copies files which are in a directory structure (e.g., hierarchical picture collections) into the root directories of the floppies. The original directory structure will be lost. The tool will only switch to the next floppy as soon as one is full, therefore this is pretty space efficient.
- Mode 2: As mode 1, but starts a new floppy for each directory being processed. This is NOT space efficient, but it kind of preserves the "grouping" of the original directory structure.
- Mode 3: Preserves the original structure and switches to a new floppy when running out of space.
- Mode 4: If you already have the contents of various floppy disks in separate directories (none larger than 1.44MB!), you can copy each directory onto one virtual floppy. This is useful for making installation disks (think of DOS, Windows) or any other software available on virtual floppies.

## Notes
- I have no relationship whatsoever with the company Gotek. The tool contains the name in the hope that it will be found and considered useful.
- Before using a new USB stick, delete the existing partition. In my case, not doing this caused the script failing to detect the correct file system of the virtual floppies. After that, partition/format the stick in your Gotek drive by keeping both buttons pressed when turning the unit on.
- I recommend using my script only for bulk-loading data, starting at floppy 1, and to keep floppy 0 ("FDISK000") free for easy occasional file exchange on floppy 0 (as this one can be mounted automatically on most computers). Also see below.

## Known Issues
- At least on my KUbuntu 17.10 machine using the script creates new "Loop Device" entries in the left side bar of the Dolphin file manager. They disappear once you unmount the FDISK000 partition and close the Dophin window. Does anybody know how to improve this?
- My script appears to only work after the first partition ("FDISK000") has been mounted (the Dolphin file manager does this automatically). I don't know if accessing this first partition (virtual floppy 0) with my script could cause trouble. That's the second reason why I recommend using my script only AFTER the first partition (starting with virtual floppy 1).
