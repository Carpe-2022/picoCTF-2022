# Packets Primer

## Description

Download the packet capture file and use packet analysis software to find the flag: https://artifacts.picoctf.net/c/200/network-dump.flag.pcap

Hint: Wireshark, if you can install and use it, is probably the most beginner friendly packet analysis software product.

## Approach

We are provided with a PCAP file. Opening this in Wireshark and analyzing the TCP stream (in stream 0) reveals the flag: `p i c o C T F { p 4 c k 3 7 _ 5 h 4 r k _ b 9 d 5 3 7 6 5 }`

Removing the spaces we get: picoCTF{p4ck37_5h4rk_b9d53765}
