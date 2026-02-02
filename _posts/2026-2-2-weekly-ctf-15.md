# Weekly CTF
This is the new semester and I am once again posting my CTFs whenever we meet.

We also went over setting up a VM.

## substitution2
[substitution2](https://play.picoctf.org/practice/challenge/309?page=1&search=substitution)

Here, it is a substitution cipher. Best way to discern something is looking at the frequency of letters. 

I used this tool for making it easier `https://www.boxentriq.com/ciphers/substitution-cipher` to see which mapping makes the most sense to get some English words out of this. But this would work just as fine by using `sed` and `tr`.

In fact, rather than keeping on using `sed`, we could use a single `tr` command with the mappings in order as such to shorten it:

    cat message.txt | tr [abcdefghijklmn] [bcdefghijklmno] > message2.txt

This command is the same as:

    sed -i 's/a/b/g' message.txt
    sed -i 's/b/c/g' message.txt
    sed -i 's/c/d/g' message.txt
    sed -i 's/d/e/g' message.txt
    sed -i 's/e/f/g' message.txt
    sed -i 's/f/g/g' message.txt
    ...

But to get the English words, we would have to use single character substitution first anyways.

Tools used:

https://wordcounter.net/character-count (Character Count)

https://www.boxentriq.com/ciphers/substitution-cipher (Can keep track of character mapping and character frequency)

Linux commands `cat`, `sed`, `tr` (for translate)

Example of above:

    sed -i 's/f/e/g' message.txt (Replaces all f's with e's globally in that file, flag -i to edit that file)
    cat message.txt | tr [:upper:] [:lower:]
    cat message.txt | tr [A-Z] [a-z] > message.txt (This overwrites the initial file)