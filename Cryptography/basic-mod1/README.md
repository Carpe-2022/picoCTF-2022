# basic-mod1

## Description

We found this weird message being passed around on the servers, we think we have a working decryption scheme.
Download the message here.
Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.
Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

## Approach
From the file, a list of integers are found:
91 322 57 124 40 406 272 147 239 285 353 272 77 110 296 262 299 323 255 337 150 102 

## The Code
```
#cipher values
cipher = [91, 322, 57, 124, 40, 406, 272, 147, 239, 285, 353, 272, 77, 110, 296, 262, 299, 323, 255, 337, 150, 102 ]

#decipher table
decipherTable = ["A", "B", "C", "D", "E", "F", "G", "H", "I","J", "K", "L", "M", "N", "O", "P", "Q", "R","S", "T", "U", "V", "W", "X", "Y", "Z", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "_"]

#print
for character in range (len(cipher)):
    print(decipherTable[cipher[character]%37],sep=' ', end='', flush=True)
```

## Solution
R0UND_N_R0UND_ADD17EC2 -> picoCTF{R0UND_N_R0UND_ADD17EC2}


