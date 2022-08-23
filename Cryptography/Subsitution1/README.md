# Subsitution1

## Description

A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.
Download the message here.

## Approach
From the file, a bunch of unreadable text was found:
```
WYHg (gzray hra wimybas yzs hvij) ias i yums rh wrombysa gswbakyu wromsykykrl. 
Wrlysgyilyg ias masgslysn dkyz i gsy rh wzivvsljsg dzkwz ysgy yzska wasiykxkyu, 
yswzlkwiv (iln jrrjvklj) gckvvg, iln marqvso-grvxklj iqkvkyu. Wzivvsljsg bgbivvu 
wrxsa i lboqsa rh wiysjraksg, iln dzsl grvxsn, siwz uksvng i gyaklj (wivvsn i hvij) 
dzkwz kg gbqokyysn yr il rlvkls gwraklj gsaxkws. WYHg ias i jasiy diu yr vsial i 
dkns iaaiu rh wrombysa gswbakyu gckvvg kl i gihs, vsjiv slxkarlosly, iln ias 
zrgysn iln mviusn qu oilu gswbakyu jarbmg iarbln yzs dravn hra hbl iln maiwykws.
Hra yzkg marqvso, yzs hvij kg: mkwrWYH{HA3FB3LWU_4774WC5_4A3_W001_7II384QW}
```

Since the challenge hints at using the same cipher as `Subsitution0`, I approached the problem in a similar way.
Since no subsitution alphabet is presentm I assumed a common string of `picoCTF` and passed the text into a monoalphabetic subsitution cipher which decoded the message.

## Solution
PICOCTF{FR3XU3NCY_4774CJ5_4R3_C001_7AA384BC}

The text deciphers to:
```
CTFS (SHORT FOR CAPTURE THE FLAG) ARE A TYPE OF COMPUTER SECURITY COMPETITION. CONTESTANTS ARE PRESENTED WITH A SET OF CHALLENGES WHICH TEST THEIR CREATIVITY, TECHNICAL (AND GOOGLING) SJILLS, AND PROBLEM-SOLVING ABILITY. CHALLENGES USUALLY COVER A NUMBER OF CATEGORIES, AND WHEN SOLVED, EACH YIELDS A STRING (CALLED A FLAG) WHICH IS SUBMITTED TO AN ONLINE SCORING SERVICE. CTFS ARE A GREAT WAY TO LEARN A WIDE ARRAY OF COMPUTER SECURITY SJILLS IN A SAFE, LEGAL ENVIRONMENT, AND ARE HOSTED AND PLAYED BY MANY SECURITY GROUPS AROUND THE WORLD FOR FUN AND PRACTICE. FOR THIS PROBLEM, THE FLAG IS: PICOCTF{FR3XU3NCY_4774CJ5_4R3_C001_7AA384BC}
```






