# Weely CTF 18
Today, we are doing more Cryptography challenges on picoCTF.

## Hashcrack 
By connecting to the server, we are to give the password from the hash identified.

For this one, we are introduced to `John The Ripper` and `hashcat`. We can also use any online hash identifier to get the hash type first or guess the hash type by looking at its structure along with some documentation like https://en.wikipedia.org/wiki/Cryptographic_hash_function.

For John, we got access to `rockyou.txt` which is a very big list of common passwords. There are other password files as well. You can get more at https://github.com/danielmiessler/SecLists/tree/master/Passwords

The command I used is:

    john --show --wordlist=rockyou.txt --format=raw-md5 password.txt

This is specifically for cracking MD5 hashes. Just change the command as fit. `--show` is to show the cracked passwords for a given hash file. Note that wordlist mode and single mode are two different modes (single mode uses username and system data and heavily mingles with these and tries them out). To get the format, look at `--list=formats`

For the rules, it is like a seperate language to generate our own rules. The default ones are already at `/etc/john/john.conf` if john is installed (so build it from here). These rules apply to the wordlist given, so you use it with wordlist mode.

More on hashcat at https://hashcat.net/wiki/ 

More on John at https://www.openwall.com/john/doc/