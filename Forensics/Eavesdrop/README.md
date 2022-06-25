# Eavesdrop

## Description

Download this packet capture and find the flag.
* [Download packet capture](https://artifacts.picoctf.net/c/359/capture.flag.pcap)

Hint: All we know is that this packet capture includes a chat conversation and a file transfer.

## Approach

This challenge involves more packet capture analysis. After downloading the file and following TCP streams, we can identify a conversation. The important parts are listed below:
`*sigh* openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123`

`Oh great. Ok, over 9002?`
Through this we learn, the method used to decrypt a file. This file was sent again as implied in the conversation. After looking through stream 2, we identify an encrypted file. Saving this file as raw packets (important) and running the command mentioned previously reveals the desired file.

```
$ cat file.txt

picoCTF{nc_73115_411_dd54ab67}
```
The flag is: picoCTF{nc_73115_411_dd54ab67}
