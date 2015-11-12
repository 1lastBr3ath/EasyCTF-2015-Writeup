Forensics
-------------

An apple a day keeps the dinosaur away? - 35 points 
-----------------
Oh look, it's a perfectly innocent picture of an [apple](https://www.easyctf.com/static/problems/apple/apple.jpg). Nothing to see here!

**Hint**:<br/>
Apples are suspicious. Don't trust apples. They always have something to hide . . .

This was amongst the easiest one. I downloaded the image, and read its content using `strings` & piped through `grep`. That did the work.
```
$strings apple.jpg | grep easyctf
   the flag is easyctf{w0w_much_appl3s}
```
Flag: `easyctf{w0w_much_appl3s}`

-------------

Liar - 50 points
-----------------
I may or may not have illegally bought this [file](https://www.easyctf.com/static/problems/png/secret) from someone who claims that it contains secret pictures of my friend and her fiancé. Unfortunately, I can't open it, and I already paid $4096 for it. Can you help me find out if the seller was lying?

**Hint**:
I feel like something is missing . . .





A Picture is Worth a Thousand Words - 100 points
--------------

A picture is worth a thousand words. Can you find the (JPEG) picture among a thousand files? Connect to the EasyCTF SSH server and find the files in `/problems/1000words`. The files are also available for download [here](https://www.easyctf.com/static/problems/1000words/data.zip).

**Hint**:<br/>
Grep is always your friend.

Here, we were provided 1000+ files, each with random name, and with no file extension. We could also download the file from given link. I tried solving it by connecting to the SSH. It was easier to find the JPEG image, just tried;

```
$file * | grep JPEG
UgeVjTlmZjNFvULk: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 266x71, frames 3
```

I found the image, however there were no flags in it. I tried reading its content using `cat` and `strings`, and they were of no help. Finally, I decided to download the file given in question, and opened the image. And, there it was.

Flag: `easyctf{it_must_be_pretty_hard_reading_this}`

-------------


Who is this god? - 175 points
---------------------------
My friend Mich uses this nice tulip as her profile pic because she likes historical stuff. Did I mention that one of the EasyCTF developers worships her as a god?

**Hint**: A tulip a day keeps the economy away :)<br/>
P.S. Everything you need is in the image...although you might need sharper vision.

It took me long enough to solve, but still, it's fairly easy. The problem gives us a picture, of tulip. (The other hint, that says, you might need sharper vision, was added later).

Since we only have a picture, I first tried reading the file using `strings`.

`$strings tulip.png`

There was nothing. I then tried finding if it was hiding something by comparing file signature, using `gHex`, still got nothing. However, at last, I realized that the problem says it all. It's a '**Forensics**' problem. That's it, I only needed a forensics tool, I found one at http://29a.ch/photo-forensics/#forensic-magnifier.

There, I only needed to load the image.

Flag: `easyctf{all_hail_michy}`
