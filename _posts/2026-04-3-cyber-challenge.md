# Cyber Challenge
Today, we are doing Operation Deadlock from Tulane University. It is a 4-hour cyber competition. 

All flags are in `DEADLOCK{}` format.

## Solves
These are the challenges that I was able to solve. Unfortunately, I could not do all of the writeups since my access got restricted pretty quickly afterwards, so I don't really remember which files are for which challenges, especially the websites for the web challenges.

### WHOIS Are You? (OSINT)
- I am given a WHOIS dump of a domain name. At the end of it, there is an "Analyst Note" of a base64-encoded artifact. Using CyberChef to decode this string, it reveals the flag.

### Picture Perfect (OSINT)
- For this one, I am given a .json file, consisting of an IP address, the hostname, opened ports and their related services. At the end, there is also an "Analyst Note" with a seemingly hexadecimal-encoded string. With CyberChef, decoding this string reveals the flag.
### Phantom Server (OSINT)
### Login.exe (Web)
### Hidden in Plain Sight (Web)
### Cookie Monster (Web)
### Ransom Note (Crypto)
- I am given a "ransom note" that is decoded. It looks to be in letter format. There is the flag, but is encoded in the middle. After looking around, I guess that it seems to be encoded with ROT13 and so, using CyberChef, I get the flag. 
- For this challenge, my teammate gave me a hint to help with choosing the cipher.

### Rabbit Hole (Crypto)
- Here, I am given an "intercepted message", which is a long string. Under it, there is a note that says to "work from outside in" and there are "three layers". This means the flag was encoded three times. Therefore, booting up CyberChef, I start looking at the patterns and after a while, the decoding is, in order, hexadecimal, Base64, and then ROT13 to get the flag.

### Operation Shutdown (Forensics)
### Paper Trail (Forensics)
### Access Granted (Forensics)
### Dead Drop (Forensics)
### Crack the Panel (Reverse Engineering)
- Note that for this challenge, especially, I did this on my own even though my teammate already got it before me.
- The file is a binary file. Using `file`, it is specifically an ELF executable. After initially running this file (from giving it permissions first to execute), it requires some passwords. With the first pass to `string`, apparently the flag is already hard-coded so I can get it out.