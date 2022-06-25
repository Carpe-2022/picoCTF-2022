# St3g0

## Description

Download this image and find the flag.
* [Download image](https://artifacts.picoctf.net/c/422/pico.flag.png)

Hint: We know the end sequence of the message will be `$t3g0`.

## Approach

Finally I get to use one of the little tools I had installed in preparation for the competition. We can download the image and use `zsteg`, a steganography tool for PNG and BMP files. The `-a` parameter attempts all known methods, and `-v` runs the command verbosely.
```
$ zsteg -a -v pico.flag.png

b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_a1062667}$t3g0"
    00000000: 70 69 63 6f 43 54 46 7b  37 68 33 72 33 5f 31 35  |picoCTF{7h3r3_15|
    00000010: 5f 6e 30 5f 35 70 30 30  6e 5f 61 31 30 36 32 36  |_n0_5p00n_a10626|
    00000020: 36 37 7d 24 74 33 67 30  00 00 00 00 00 00 00 00  |67}$t3g0........|
    00000030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
    *
    000000f0: 00 00 00 00 01 42 f3 6d  b6 db 6d b6 db 6d b6 db  |.....B.m..m..m..|
b1,abgr,lsb,xy      .. text: "E2A5q4E%uSA"
    00000000: 61 03 15 16 66 31 45 21  24 17 51 37 62 06 45 32  |a...f1E!$.Q7b.E2|
    00000010: 41 35 71 34 45 25 75 53  41 05 71 35 61 06 00 30  |A5q4E%uSA.q5a..0|
    00000020: 66 15 75 14 41 a6 00 3b  49 96 60 b3 4d b7 b1 99  |f.u.A..;I.`.M...|
    00000030: ed 06 45 17 41                                    |..E.A           |
b2,b,lsb,xy         .. text: "AAPAAQTAAA"
[...]
```
The flag is revealed: picoCTF{7h3r3_15_n0_5p00n_a1062667}
