# gb01print

Python script to print images to the GB01 printer from the command line.

The GB01 is a small Bluetooth thermal printer that uses receipt paper. 
I don't know if it's been built into other cases, but mine kind of looks like a cat.
You can tell it's a GB01 because it shows up as a Bluetooth device called "GB01" when you scan for it.

This script takes a filename as its only required parameter. 
It will attempt to load the file as an image, 
connect to the first Bluetooth low energy device called "GB01" it finds,
and print the image.

    usage: gb01print.py [-h] [-l | -m | -d] [-A ADDRESS] [-D] [-t THROTTLE | -T] [-p PACKETSIZE] filename
    
    Prints a given image to a GB01 thermal printer.
    
    positional arguments:
      filename              file name of an image to print
    
    optional arguments:
      -h, --help            show this help message and exit
      -e, --eject           don't print an image, just feed some blank paper
      -E, --no-eject        don't feed blank paper after printing the image     
      -l, --light           use less energy for light contrast
      -m, --medium          use moderate energy for moderate contrast
      -d, --dark            use more energy for high contrast
      -A ADDRESS, --address ADDRESS
                            MAC address of printer in hex (rightmost digits, colons optional)
      -D, --debug           output notifications received from printer, in hex
      -t THROTTLE, --throttle THROTTLE
                            delay between sending command queue packets, in seconds
      -T, --no-throttle     don't wait while sending data
      -p PACKETSIZE, --packetsize PACKETSIZE
                            length of a command queue packet, in bytes
