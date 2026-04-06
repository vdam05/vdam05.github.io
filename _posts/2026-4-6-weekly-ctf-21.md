# Weekly CTF 21
Today, we are just doing any picoCTF challenges, not much in mind. The clubtime didn't start for 30 minutes.

## Trickster
[Trickster](https://play.picoctf.org/practice/challenge/445?page=1&search=trickster)

For this one, it is a file upload vulnerability. We are given a place to upload only .png files. First, we can test somethings out. We can write a simple webshell PHP file and upload it. Then, we see that it requires a PNG file. 

Okay, then let's try to upload the PHP webshell with extension `.png`. It says that it has an error and displays some hexadecimal values. Then, I look at the hex values of the file with `xxd` and see that it checks for the magic bytes of a PNG as a validation method. 

Therefore, we could add the PNG magic bytes in front so that it accepts it as a .png file. This can be done via Burp Suite or Python. Burp Suite makes it easier to edit the content of the file and the name of the file. Sure, it bypasses the check, but when we go to `./uploads/filename.png` to try and run it, it won't run because it is a PNG.

Then, I found a good resource for reference: https://www.synacktiv.com/publications/persistent-php-payloads-in-pngs-how-to-inject-php-code-in-an-image-and-keep-it-there

Also, I look at the `robots.txt` file. There is `/uploads` which we guessed and there is `/instructions.txt`. Going there, we basically get a confirmation of the server behavior: it checks extension and header bytes.

Wait a minute, it says it looks for a `.png` extension. Does it say that the extension needs to be at the end? If not, we can use our PNG file with the magic bytes added and make it into a PHP file like `file.png.php`.

After uploading, it works and now we can look for the flag file with a combination of `ls` and `cat`, appending multiple commands into one line with `;`.

Note: I ran out of clubtime and looked for some hints for this challenge so I could finish it.