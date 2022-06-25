# Sleuthkit Apprentice

## Description

Download this disk image and find the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
* [Download compressed disk image](https://artifacts.picoctf.net/c/331/disk.flag.img.gz)

## Approach

First, we can extract the disk image using `gunzip disk.flag.img.gz`. We can then use Autopsy to find the flag in this challenge. Autopsy is the GUI of Sleuthkit. 

After initial setup of the project, we can conduct file analysis on the `/3/` partition. If we search for any file with the name `flag`, we will find two files. Going through these will display the flag: picoCTF{by73_5urf3r_25b0d0c0} 
