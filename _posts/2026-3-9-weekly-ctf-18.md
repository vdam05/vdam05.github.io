# Weekly CTF 18
Today, we were supposed to be doing a variety of challenges in different categories on picoCTF, but there is some sort of server errors. So we are doing challenges without spinning up an instance.

# New Viginere
We are continuing this one from Weekly CTF 16.

The first method is called `b16_encode` and taking a look at it, it takes each character in the plaintext, formats it as an 8-bit representation, then converts each half into an integer (the second argument of int() tells us the base that the first argument is in) annd turns it to be one of the character in `ALPHABET`.

On line 18-23, we also get a hint on what the key and flag should be. The characters in the flag should be one of these: `abcdef0123456789`. The ones in the key should be from the ALPHABET and its length is less than 15.

Note that `enumerate()` gets both the index and element in the loop.

A group member points out something interesting, where in binary form, some characters have the same upper half, like `a` and `b`. Therefore, I wrote a script to look at all the characters allowed in the flag in binary form and also the characters in the plaintext and their indices.

Ran out of time again during the meeting.