# File types

## Description

This file was found among some files marked confidential but my pdf reader cannot read it, maybe yours can.
You can download the file from here: https://artifacts.picoctf.net/c/324/Flag.pdf 

Hint: Remember that some file types can contain and nest other files

## Approach

The file provided is in PDF format, but it is unopenable. The hint lets us know that this challenge involved nested files. 

`file Flag.pdf` shows that it is a shell archive. Executing this creates a file named `flag`

Next, we will inspect this file through binwalk: 

```
$ binwalk flag

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
100           0x64            bzip2 compressed data, block size = 900k
```
This reveals the file is compressed through the bzip2 algorithm. We can now extract this:

```
$ binwalk -e flag
$ ls

Flag.pdf _flag.extracted  flag 

$ cd _flag.extracted/

$ ls

64
```
After extraction, a new folder named `_flag.extracted` is created. Inside the folder is a file called `64`.

`file 64` reveals that the file is compressed through gzip. We can now extract again using binwalk: `$ binwalk -e 64`, which reveals a new file named flag in the directory.

Checking the file again reveals it is compressed through lzip. We can extract by doing `$ lzip -d -k flag`. `-d` will decompress, while `-k` keeps the original file. This creates a file named `flag.out`

The same (and tedious) process reveals it is compressed through LZ4. We can extract by doing `$ lz4 -d flag.out flag_2.out`, which will decompress the file. This process continues through LZMA, LZOP, LZIP, and XZ with the end result being ASCII text: 

`7069636f4354467b66316c656e406d335f6d406e3170756c407431306e5f
6630725f3062326375723137795f33343765616536357d0a`

This hex decodes to the flag: picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_347eae65}
