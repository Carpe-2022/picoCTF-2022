# Subsitution0

## Description

We found a leak of a blackmarket website's login credentials. Can you find the password of the user cultiris and successfully decrypt it?
Download the leak here.
The first user in usernames.txt corresponds to the first password in passwords.txt. The second user corresponds to the second password, and so on.

## Approach
From the file, a bunch of unreadable text was found. However, locating the username `cultiris` was simple. 
```
`cultiris` was a username that corresponded with this password: 

cvpbPGS{P7e1S_54I35_71Z3}
```
Since the cipher text is aleady in the correct format, I assumed a shift cipher is used.
After testing out all the shifts, a shift of 13 gave a reasonable answer:picoCTF{C7r1F_54V35_71M3}


## Solution
picoCTF{C7r1F_54V35_71M3}


