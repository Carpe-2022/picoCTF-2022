# Redaction gone wrong

## Description

Now you DON’T see me.
This [report](https://artifacts.picoctf.net/c/264/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

Hint: How can you be sure of the redaction?

## Approach

One of the quirks with redaction is that sometimes the text is only visually hidden from view, while the data still remains. The text can be retrieved simply by selecting the redacted text.

The last redacted section reveals the flag: picoCTF{C4n_Y0u_S33_m3_fully}
