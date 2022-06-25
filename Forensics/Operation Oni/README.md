# Operation Oni

## Description

Download this disk image, find the key and log into the remote machine.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

## Approach

A challenge instance is provided. As we are attempting to ssh into the remote machine, we should be looking for an ssh key. We can first extract the disk, then use Sleuthkit to analyze.

```
$ mmls disk.img 

DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```
Accessing partition 003:
```
$ fls -o 206848 disk.img

d/d 458:	home
d/d 11:	lost+found
d/d 12:	boot
d/d 13:	etc
d/d 79:	proc
d/d 80:	dev
d/d 81:	tmp
d/d 82:	lib
d/d 85:	var
d/d 94:	usr
d/d 104:	bin
d/d 118:	sbin
d/d 464:	media
d/d 468:	mnt
d/d 469:	opt
d/d 470:	root
d/d 471:	run
d/d 473:	srv
d/d 474:	sys
V/V 33049:	$OrphanFiles
```
We can use `fls -o 206848 disk.img 470` to access the `root` directory.
```
$ fls -o 206848 disk.img 470

r/r 2344:	.ash_history
d/d 3916:	.ssh
```
Surely enough, there is a directory named `.ssh`. We can do the same thing with this:
```
$ fls -o 206848 disk.img 3916

r/r 2345:	id_ed25519
r/r 2346:	id_ed25519.pub
```
Here are the SSH key files. We can retrieve the private key by using `icat` and save it locally.
```
$ icat -o 206848 disk.img 2345

-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLAAAAJgxpYKDMaWC
gwAAAAtzc2gtZWQyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLA
AAAECItu0F8DIjWxTp+KeMDvX1lQwYtUvP2SfSVOfMOChxYGCtd7hso2E7OQItY6aTjMMy
KZb1FVmeBfnVjyHcGYosAAAADnJvb3RAbG9jYWxob3N0AQIDBAUGBw==
-----END OPENSSH PRIVATE KEY-----
```
Note that we must change the permissions of the file to satisfy SSH security rules: `chmod 400 local.key`

We can now connect to the remote machine: `ssh -i local.key -p 60025 ctf-player@saturn.picoctf.net`. `ls` reveals `flag.txt`, which contains the flag: picoCTF{k3y_5l3u7h_af277f77}
