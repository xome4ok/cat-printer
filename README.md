# gb01print

Python script to print images to GB01/MX06 printer from the command line.

The GB01/MX06 is a small Bluetooth thermal printer that uses receipt paper. 
I don't know if it's been built into other cases, but mine kind of looks like a cat.
You can tell it's a GB01/MX06 because it shows up as a Bluetooth device called "GB01" or "MX06" when you scan for it.

This script takes a filename as its only required parameter. 
It will attempt to load the file as an image, 
connect to the first Bluetooth low energy device called "GB01" or "MX06" it finds,
and print the image.

## What's new in this fork?

### C(h)atting to cat printer

See, it's a cat printer. That means you should be able to cat something to it.

Run `python gb01print.py --pipe cat_printer`, and it will create a named pipe called `cat_printer` in the current directory.

Now, when you go `cat cat.txt > cat_printer` you cat to cat printer and it prints your cats!

### Printing text

> [!NOTE]
> Text rendering is implemented thanks to [this gist](https://gist.github.com/mpomery/6514e521d3d03abce697409609978ede)

Another new option is passing a text file, not an image.

It goes like this: `python gb01print.py --assume-text cat.txt`.



    usage: gb01print.py [-h] [-e] [-E | -f LINES] [--header LINES] [--scale-feed] [-l | -m | -d] [-A ADDRESS] [-D] [--assume-text] [--pipe]
                        [-t SECONDS | -T] [-p BYTES]
                        [filename]

    Prints a given image to a GB01 thermal printer.

    positional arguments:
      filename              file name of an image to print

    options:
      -h, --help            show this help message and exit
      -e, --eject           don't print an image, just feed some blank paper
      -E, --no-eject        don't feed blank paper after printing the image
      -f LINES, --feed LINES
                            amount of blank paper to feed (default: 55)
      --header LINES        feed blank paper before printing the image
      --scale-feed          adjust blank paper feed proportionately when resizing image
      -l, --light           use less energy for light contrast
      -m, --medium          use moderate energy for moderate contrast
      -d, --dark            use more energy for high contrast
      -A ADDRESS, --address ADDRESS
                            MAC address of printer in hex (rightmost digits, colons optional)
      -D, --debug           output notifications received from printer, in hex
      --assume-text         assume that file type is text
      --pipe                treat the file as a continous pipe, listen to it and output everything to printer
      -t SECONDS, --throttle SECONDS
                            delay between sending command queue packets (default: 0.01)
      -T, --no-throttle     don't wait while sending data
      -p BYTES, --packetsize BYTES
                            length of a command queue packet (default: 60)
