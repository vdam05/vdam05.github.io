# Cyber Challenge
Today, we are doing Operation Deadlock from Tulane University. It is a 4-hour cyber competition. 

All flags are in `DEADLOCK{}` format.

## Solves
These are the challenges that I was able to solve. Unfortunately, I may or may not be able to do all of the writeups since my access got restricted pretty quickly afterwards, so I don't really remember which files are for which challenges, especially the websites for the web challenges.

I do try to write accurate writeups though. These writeups are accurate for the challenges that I did. I left out writeups for challenges I don't really remember.

### WHOIS Are You? (OSINT)
- I am given a WHOIS dump of a domain name. At the end of it, there is an "Analyst Note" of a base64-encoded artifact. Using CyberChef to decode this string, it reveals the flag.

### Picture Perfect (OSINT)
- This one provides a `.png` file and there seems to be a flag in there. Even though it requires us to use some tools like `exiftool` to look at the metadata of this image for the flag, I just use `cat` and the flag is intact with it. 

### Phantom Server (OSINT)
- For this one, I am given a .json file, consisting of an IP address, the hostname, opened ports and their related services. At the end, there is also an "Analyst Note" with a seemingly hexadecimal-encoded string. With CyberChef, decoding this string reveals the flag.

### Login.exe (Web)
- This challenge has a simple SQL injection vulnerability in its login page, just using this in its fields:

    username: ' OR 1=1 -- -
    password: abc

This bypasses the credential check and gives the flag.

### Hidden in Plain Sight (Web)

### Cookie Monster (Web)
- With this challenge, there is no need to guess credentials since they are already given, but the challenge requires that I log in as a superadmin, rather than just a user, to see the secrets (which would be the flag). 
- First off, I try to intercept the packet using `Burp Suite` and see the POST parameters of this HTTP packet. There is a field `login=1` before `username` and `password`. I think that this value may dictate access, as in higher or lower values mean more permission. Trying some values out like 1, 2, 100, -1, it doesn't seem to be the case. 
- I then look at the HTML, with `Inspect Mode`, and do not see much to it. But then, I delve through it and look at the `Cookies` in `Application`. Perhaps, the cookies have something to do with it. There is a cookie called something like `sessionId`, and it seems to be base64-encoded. Decoding it (with CyberChef) yields a JSON-formatted string, with a key-value pair as `role: user`. This is big information, this means the cookie value determines access level. Therefore, replacing this pair to `role: superadmin`, re-encoding the entire cookie in Base64, using this new cookie value, and finally refreshing the page would allow me to gain access to the flag as a superadmin and not a user. 

### Ransom Note (Crypto)
- I am given a "ransom note" that is decoded. It looks to be in letter format. There is the flag, but is encoded in the middle. After looking around, I guess that it seems to be encoded with ROT13 and so, using CyberChef, I get the flag. 
- For this challenge, my teammate helped me with deciding the cipher.

### Rabbit Hole (Crypto)
- Here, I am given an "intercepted message", which is a long string. Under it, there is a note that says to "work from outside in" and there are "three layers". This means the flag was encoded three times. Therefore, booting up CyberChef, I start looking at the patterns and after a while, the decoding is, in order, hexadecimal, Base64, and then ROT13 to get the flag.

### Operation Shutdown (Forensics)
- For this one, I am given a disk image. Passing it to `mmls`, nothing pops up so there is no partition here to worry about. Then, using `fls`, I see that there are 4 files, with 1 file called "encryption_master.txt" that is deleted. However, it is recoverable  and via `tsk_recover`, the flag is in that file that was deleted.
- These tools are from The Sleuth Kit (TSK).

### Paper Trail (Forensics)
- This challenge gives me a `.xml` file that seems to be a dump of the processes on a computer. Therefore, it asks that we identify a malicious process in here and give the name of the process and its time in HH-MM-SS as part of the flag. Looking through it, there is a suspicious `d34dl0ck_crypt.exe` file in one of the process and the flag is correct for it.

### Access Granted (Forensics)
### Dead Drop (Forensics)
- There is a `.pcap` file provided so I am doing some network forensics here. There is a bunch of HTTP, TCP and DNS packets here. The HTTP packets don't seem to have much interesting in the packet byte window, so I follow the TCP stream to reassemble the packets in the right order. There is an `Encryption key (base64)` that stood out the most and base64-decoding it gives the DEADLOCK flag. 

### Crack the Panel (Reverse Engineering)
- Note that for this challenge, especially, I did this on my own even though my teammate already got it before me.
- The file is a binary file. Using `file`, it is specifically an ELF executable. After initially running this file (from giving it permissions first to execute), it requires some passwords. With the first pass to `string`, apparently the flag is already hard-coded so I can get it out.