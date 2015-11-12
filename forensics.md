Forensics
-------------

Who is this god? - 175 points
---------------------------
My friend Mich uses this nice tulip as her profile pic because she likes historical stuff. Did I mention that one of the EasyCTF developers worships her as a god?

**Hint**: A tulip a day keeps the economy away :)<br/>
P.S. Everything you need is in the image...although you might need sharper vision.

It took me long enough to solve, but still, it's fairly easy. The problem gives us a picture, of tulip. (The other hint, that says, you might need sharper vision, was added later).

Since we only have a picture, I first tried reading the file using `strings`.

`$strings tulip.png`

There was nothing. I then tried finding if it was hiding something by comparing file signature, using gHex, still got nothing. However, at last, I realized that the problem says it all. It's a 'Forensics' problem. That's it, I only needed a forensics tool, I found one at http://29a.ch/photo-forensics/#forensic-magnifier.

There, I only needed to load the image.

Flag: `easyctf{all_hail_michy}`
