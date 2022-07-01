# Rail-fences

## Description

A type of transposition cipher is the rail fence cipher, which is described here. Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?
Download the message here.
Put the decoded message in the picoCTF flag format, picoCTF{decoded_message}.

## Approach
After reading through what a rail fence cipher is, it became clear what I had to do. I found a [rail-fence decoder online](https://www.dcode.fr/rail-fence-cipher)
and set the rail count to 4, and checked the box which kept punctuation and spaces. This gave the the decoded message: `The·flag·is:·WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7`

## Solution
picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7}


