# GotekTool
Linux Bash script to mass-copy files to USB sticks that have been formatted for Gotek USB floppy drive emulators.

The Gotek USB floppy disk drive emulators are excellent products. They allow you tp upgrade old floppy-based hardware with USB storage capabilities. Unfortunately, the available (Windows only) software is a bit awkward to use, because you have to first copy your files manually into directories and then sync all directories with the USB stick. It is also difficult to estimate how much data can go onto one virtual floppy, therefore your are very likely to waste space.

This Linux script copies files to USB sticks formatted for the Gotek drive. It automatically switches to the next floppy disk when one is full. Several options are available for handling directories (see below). After uploading data to an USB stick, an index text file is created so that you can find the files quickly later on.

I programmed this script to copy large amounts of style files to my Yamaha PSR-8000 keyboard. It makes the provision of files via a USB stick a breeze.

Attention: The script must be adjusted before use (mounting point and device must be changed if necessary). Use at your own risk!!


    GotekTool - A Batch File Copier for Gotek USB Floppy Disk Emulators
    Copyright 2017 Sebastian Mate

               Usage: gotektool SOURCEDIRECTORY STARTFLOPPY MODE

     SOURCEDIRECTORY: The base directory to be copied.
         STARTFLOPPY: The number of the first virtal floppy.
                MODE: The mode of file handling, which is:
                      1 = Flatten directories and copy all files to the root directory of the virtual floppies.
                      2 = As 1, but also change floppy for each directory.
                      3 = Preserve original directory structures.
                      4 = Move contents from base directories to separate virtual floppies.

          WARNING: This tool does erase data on the target device and is potentially dangerous.
                   Use on your own risk!
