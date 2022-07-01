# basic-mod2

## Description

A new modular challenge!
Download the message here.
Take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

## Approach
From the file, a list of integers are found:
`104 85 69 354 344 50 149 65 187 420 77 127 385 318 133 72 206 236 206 83 342 206 370`

In order to get the cipher message, we need to mod each value by 41 and find the modular inverse.

## The Code
```
#cipher values
cipher = [104, 85, 69, 354 ,344 ,50 ,149, 65 ,187 ,420, 77 ,127, 385, 318 ,133 ,72 ,206, 236 ,206 ,83 ,342 ,206 ,370 ]

#decipher table
decipherTable = ["","A", "B", "C", "D", "E", "F", "G", "H", "I","J", "K", "L", "M", "N", "O", "P", "Q", "R","S", "T", "U", "V", "W", "X", "Y", "Z", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "_"]

#modular inverse function
def modFun(a, m):
    for x in range(1, m):
        if (((a%m) * (x%m)) % m == 1):
            return x
    return -1

#print
for character in range (len(cipher)):
    print(decipherTable[modFun(cipher[character], 41)],sep=' ', end='', flush=True)
```

## Solution
1NV3R53LY_H4RD_DADAACAA -> picoCTF{1NV3R53LY_H4RD_DADAACAA}


