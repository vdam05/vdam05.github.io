# February 2026 MetaCTF Flash CTF
For this CTF challenge on `MetaCTF`, we are allowed to publish writeups of challenges solved so I am going to do that.

## Great Paywalk
This one is a simple DOM manipulation. Or just go to `Source` and find the flag in the HTML

## Dead Drop
I am using Wireshark to look at this pcap file. First off, I am walking through the packets and look at the packet bytes to see if there is anything interesting. After following the TCP stream, I see that the client is sending something to the server. Then in one of the TCP packet, the bigger ones, there is the content of a PNG file called flag.png. To extract it, go to File > Extract Objects > HTTP and extract the files.

In the main image file, I just remove any lines that are not part of the PNG at the start and end and the image gives us the flag.

Note: It didn't work on Wireshark on Windows for some reason, but did work on Ubuntu. 

# License to Rev
For this one, I am using Ghidra and Ida to figure it out. 

Updated: Didn't figure it out, ran out of time