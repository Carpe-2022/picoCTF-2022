# SideChannel

## Description

There's something fishy about this PIN-code checker, can you figure out the PIN and get the flag?
Download the PIN checker program here [pin_checker](https://artifacts.picoctf.net/c/144/pin_checker)
Once you've figured out the PIN (and gotten the checker program to accept it), connect to the master server using `nc saturn.picoctf.net 55824` and provide it the PIN to get your flag.

Hint 1: Read about "timing-based side-channel attacks."

Hint 2: Attempting to reverse-engineer or exploit the binary won't help you, you can figure out the PIN just by interacting with it and measuring certain properties about it.

Hint 3: Don't run your attacks against the master server, it is secured against them. The PIN code you get from the pin_checker binary is the same as the one for the master server.

## Approach

According to Wikipedia, a timing attack is "a side-channel attack in which the attacker attempts to compromise a cryptosystem by analyzing the time taken to execute cryptographic algorithms. Every logical operation in a computer takes time to execute, and the time can differ based on the input; with precise measurements of the time for each operation, an attacker can work backwards to the input." Let's take a look at the binary:

```
$ ./pin_checker

Please enter your 8-digit PIN code:
12345678
8
Checking PIN...
Access denied.
```
In the case of this program, when a pin is inputted, each character in the input is compared to the correct PIN. If there is an incorrect character, the program immediately stops. By measuring the time it takes, we can determine the correct PIN. We can now create a script to determine the PIN. Alternatively, we can also do this by hand.
```python
from pwn import *
import time
import numpy as np
import collections

context.log_level = 'error'
pin = ["0", "0", "0", "0", "0", "0", "0", "0"]
duration = {}

for j in range(8):
    duration.clear()
    for x in range(48, 58): # Unicode numbers
        pin[j] = chr(x)
        start_duration = time.time()
        print("PIN:", "".join(pin))
        z = process("pin_checker")
        z.sendlineafter("Code:\n", "".join(pin).encode())
        z.recvline()
        z.recvline()
        z.recvline()
        duration[chr(x)] = "{:.2g}".format(time.time() - start_duration)
        # print(duration[chr(x)])
        z.close()

    uniq = collections.Counter(duration.values()).most_common()[-1][0] # Most common values
    for key, value in duration.items():
        if uniq == value:
            pin[j] = key


print("Answer:", "".join(pin))
```
After running this script, we determine the PIN to be 48390513. We can now input this into the master server:
```
$ nc saturn.picoctf.net 55824

Please enter the master PIN code:
48390513
Password correct. Here's your flag:
picoCTF{t1m1ng_4tt4ck_eb4d7efb}
```
Thus, the flag is: picoCTF{t1m1ng_4tt4ck_eb4d7efb}
