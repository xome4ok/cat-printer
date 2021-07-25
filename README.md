# gb01print
Quick-and-dirty python script to print images to the GB01 printer from the command line.

The GB01 is a small Bluetooth thermal printer that uses receipt paper. 
I don't know if it's been built into other cases, but mine kind of looks like a cat.
You can tell it's a GB01 because it shows up as a Bluetooth device called "GB01" when you scan for it.

This script takes a filename as its only required parameter. 
It will attempt to load the file as an image, 
connect to the first Bluetooth low energy device called "GB01" it finds,
and print the image.
