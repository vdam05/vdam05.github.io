# Weekly CTF 16
Today, we are doing more cryptography-related challenges.

## viginere
[viginere](https://play.picoctf.org/practice/challenge/316?page=1&search=vigenere)

Viginere is a similar encryption method to Caesar cipher where it involves rotating characters as well.

Viginere is "a method of encrypting alphabetic text where each letter of the plaintext is encoded with a different Caesar cipher, whose increment is determined by the corresponding letter of another text, the key".

For example, if the first letter in plaintext is T and the first letter in the key is C, then it yields V by shifting T by 3 positions (C).

It is symmetric as well.

They gave us the key and the encrypted message so I can choose `Viginere Decode` on CyberChef to decrypt it.

## Custom encryption
[Custom encryption](https://play.picoctf.org/practice/challenge/412?page=1&search=custom)

Note that custom encryption is usually a bad idea

We are given an encryption file and an encrypted message. Now we have to create a decryption file and pass the message through.

It looks to be a symmetric encryption method.

In the encrypted message, we are given the values of `a` and `b` as well. We are also given the key at the end of the encryption file.

To solve this, I created a Python file called `solve.py` and figure out the rest of the variables, including `u`, `v`, `key`, `b_key`, `shared_key`.

Then I created two functions from the two encryption functions, to decrypt instead. The way to do this is to reverse it.

My code:

    def decrypt(cipher, key):  
        plain = []
        for char in cipher:
            plain.append(round(char / 311 / key))
        return plain

    def dynamic_xor_decrypt(cipher, text_key):
        text_key_len = len(text_key)
        plaintext = ""
        for i, char in enumerate(cipher[::1]): # The encryption loops from right to left and adds character from left to right. So we can reverse the order.
            key_char = text_key[i % text_key_len]
            decrypted_char = chr(char ^ ord(key_char)) # ^ is XOR
            plaintext = decrypted_char + plaintext
        return plaintext
    def generator(a, b, c):
        return pow(a,b) % c

    p = 97
    g = 31
    a = 95 # a and b are given in the encrypted message
    b = 21
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    text_key = "trudeau" # This key is shown at the end of the encryption file
    ciphertext = [237915, 1850450, 1850450, 158610, 2458455, 2273410, 1744710, 1744710, 1797580, 1110270, 0, 2194105, 555135, 132175, 1797580, 0, 581570, 2273410, 26435, 1638970, 634440, 713745, 158610, 158610, 449395, 158610, 687310, 1348185, 845920, 1295315, 687310, 185045, 317220, 449395] # This ciphertext is given in the encrypted message
    semi_decr = decrypt(ciphertext, shared_key)
    full_decr = dynamic_xor_decrypt(semi_decr, text_key)
    print(f"Shared key is: {shared_key}")
    print(f"Semi_decr is: {semi_decr}")
    print(f"Final msg is: {full_decr}")
    print(f"Length of cipher is: {len(ciphertext)}")




