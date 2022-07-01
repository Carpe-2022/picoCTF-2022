# Subsitution0

## Description

A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher?
Download the message here.

## Approach
From the file, a bunch of unreadable text was found:
```
QWITJSYHXCNDFERMUKGOPVALBZ 

Hjkjpmre Djykqet qkrgj, axoh q ykqvj qet goqojdb qxk, qet wkrpyho fj ohj wjjodj
skrf q ydqgg iqgj xe ahxih xo aqg jeidrgjt. Xo aqg q wjqpoxspd giqkqwqjpg, qet, qo
ohqo oxfj, penerae or eqopkqdxgog—rs irpkgj q ykjqo mkxzj xe q gixjeoxsxi mrxeo
rs vxja. Ohjkj ajkj oar krpet wdqin gmrog ejqk rej jlokjfxob rs ohj wqin, qet q
drey rej ejqk ohj rohjk. Ohj giqdjg ajkj jlijjtxeydb hqkt qet ydrggb, axoh qdd ohj
qmmjqkqeij rs wpkexghjt yrdt. Ohj ajxyho rs ohj xegjio aqg vjkb kjfqknqwdj, qet,
oqnxey qdd ohxeyg xeor iregxtjkqoxre, X irpdt hqktdb wdqfj Cpmxojk srk hxg rmxexre
kjgmjioxey xo.

Ohj sdqy xg: mxirIOS{5PW5717P710E_3V0DP710E_03055505}
```

Using a [monoalphabetic cipher decoder](https://www.dcode.fr/monoalphabetic-substitution), I set the key as the 1st line: `QWITJSYHXCNDFERMUKGOPVALBZ`. From there, I used the last line as the flag text, which deciphered into `THE FLAG IS: PICOCTF{5UB5717U710N_3V0LU710N_03055505}`. 


## Solution
picoCTF{5UB5717U710N_3V0LU710N_03055505}.

The rest of the text deciphers to:
```
Hereupon Legrand arose, with a grave and stately air, and brought me the beetle
from a glass case in which it was enclosed. It was a beautiful scarabaeus, and, at
that time, unknown to naturalists—roficourseqaygreatmprizexinqagscientificmpointrofvview OThereawereotwokroundwblackgspotsenearronejextremityrofothewback qandqadlongroneenearotherother OThegscalesawerejexceedinglyhhardqandyglossy awithqallotheqappearancerofwburnishedygold OTheaweightrofothexinsectawasvverykremarkable qand
otakingqallothingsxintoiconsideration XIicouldhhardlywblameCJupitersforhhisropinionkrespectingxit
```
I ignored this.

