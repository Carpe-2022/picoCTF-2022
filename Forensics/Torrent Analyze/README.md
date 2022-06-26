# Torrent Analyze

## Description

SOS, someone is torrenting on our network.
One of your colleagues has been using torrent to download some files on the company’s network. Can you identify the file(s) that were downloaded? The file name will be the flag, like `picoCTF{filename}`. [Captured traffic](https://artifacts.picoctf.net/c/206/torrent.pcap).

Hint 1: Download and open the file with a packet analyzer like Wireshark.

Hint 2: You may want to enable BitTorrent protocol (BT-DHT, etc.) on Wireshark. Analyze -> Enabled Protocols

Hint 3: Try to understand peers, leechers and seeds. [Article](https://www.techworm.net/2017/03/seeds-peers-leechers-torrents-language.html)

Hint 4: The file name ends with `.iso`

## Approach

We are provided with a packet capture file. Ensure the bittorrent protocols - specifically BT-DHT - are enabled in Wireshark, as they may not enabled by default (Analyze > Enabled Protocols). Here's a quick summary of torrenting:
* Seeds are active torrent clients that have a copy of the complete file, and are sharing.
* Peers are those who are downloading the file. 
* Filenames are identified in each packet by `info_hash`

So, we should be looking for `info_hash`. We can find all packets with this term by using the built in search function. We can also further narrow this down by looking for packets with a source address from the local network (192.168.73.132). Here is our filter: `bt-dht.bencoded.string contains info_hash and ip.src == 192.168.73.132`

The resultant packets all have the same `info_hash` value: `e2467cbf021192c241367b892230dc1e05c0580e`. A quick Google search reveals the filename: `ubuntu-19.10-desktop-amd64.iso`.

Thus, the flag is: picoCTF{ubuntu-19.10-desktop-amd64.iso}
