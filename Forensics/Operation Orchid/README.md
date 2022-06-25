# Operation Orchid

## Description

Download this disk image and find the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
* [Download compressed disk image](https://artifacts.picoctf.net/c/237/disk.flag.img.gz)

## Approach

We can mount the .img file:
```
$ fdisk -l disk.flag.img

Disk disk.flag.img: 400 MiB, 419430400 bytes, 819200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb11a86e3

Device         Boot  Start    End Sectors  Size Id Type
disk.flag.img1 *      2048 206847  204800  100M 83 Linux
disk.flag.img2      206848 411647  204800  100M 82 Linux swap / Solaris
disk.flag.img3      411648 819199  407552  199M 83 Linux

$ sudo mount -o loop,offset=210763776 disk.flag.img /mnt/

$ ls -la 

total 4
drwx------  2 root root 1024 Oct  6 14:32 .
drwxr-xr-x 22 root root 1024 Oct  6 14:30 ..
-rw-------  1 root root  202 Oct  6 14:33 .ash_history
-rw-r--r--  1 root root   64 Oct  6 14:32 flag.txt.enc
```
The `-la` option also displays hidden files. This directory shows two files: `.ash_history` and `flag.txt.enc`. We want to view flag.txt, but it is obviously encoded. `.ash_history` should show shell history as implied in the filename.
```
$ cat .ash_history

touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
```
Unfortunately, this user did not do a good job cleaning up. We now know that the file is encrypted through SSL. We can use the same command as above with the `-d` decompression option.
```
$ openssl aes256 -d -salt -in flag.txt.enc -out flag -k unbreakablepassword1234567

*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
140015604639104:error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:../crypto/evp/evp_enc.c:610:

$ ls

flag  flag.txt.enc

$ cat flag

picoCTF{h4un71ng_p457_5113beab}
```
This reveals the flag: picoCTF{h4un71ng_p457_5113beab}
