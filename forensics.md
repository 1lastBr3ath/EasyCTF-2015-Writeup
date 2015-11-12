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

This seems hard at first, but with thorough investigation, it may be solved easily. We're provided with a file that is actually a `Zip archive`. During investigation, I found that it's a [**AppleDouble Format**](https://en.wikipedia.org/wiki/AppleSingle_and_AppleDouble_formats), and there's no actual use of second file `._secret.png`. Then, I started working with first file, `secret.png`. I ran `file` to determine what exactly the file is. It showed me `data` only, whereas `png` files normally return 
`PNG image data, ......`. I wondered what it might be, opened it via `ghex`, and compared its offset bits from [Wikipedia's](https://en.wikipedia.org/wiki/List_of_file_signatures). There, it turns out to be a `png` file, but it was missing some offset bits (as the hint says). I repaired the image, inserting those missing bits, opened the image, and done. There's the flag.

```
$file secret
secret: Zip archive data, at least v2.0 to extract
$unzip secret -d dir
Archive:  secret
  inflating: secret_dir/secret.png   
   creating: secret_dir/__MACOSX/
  inflating: secret_dir/__MACOSX/._secret.png 
$cd dir
$file secret.png 
secret.png: data
$file __MACOSX/._secret.png 
__MACOSX/._secret.png: AppleDouble encoded Macintosh file
$hd secret.png | head -n1
00000000  0d 0a 1a 0a 00 00 00 0d  49 48 44 52 00 00 0a 47  |........IHDR...G|
```
According to [Wikipedia](https://en.wikipedia.org/wiki/List_of_file_signatures), `89 50 4E 47 0D 0A 1A 0A` is the offset for `png` images.

Flag: `easyctf{troll3d}`

--------------------------


lolteam - 65 points
-------------------
There's a suspicious team out there called lolteam, I got my eyes on them for a while and I managed to [wiretap](https://www.easyctf.com/static/problems/lolteam/lolteam.pcapng) their browser as they were changing their password. What did they change their password to?

**Hint**:
Don't know how to open `.pcapng` files?

Here, we're given a `.pcapng` file, which can be opened using `Wireshark`. Just selecting '**Follow TCP Stream**' from '**Analyze**' menu reveals the form data, which also includes the flag.

Flag: `easyctf{no,_lolteam_is_not_an_admin_account}`

-----------


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

Rest in Pepperoni-Pizzas - 100 points
---------------------
I gave my little sister a flag, but she cut it up and hid the pieces! Retrieve it here: [ripinpizzas.pdf](https://www.easyctf.com/static/problems/rip/ripinpizzas.pdf).

**Hint**:
Have fun! If you do it by the paper-and-scissors method, share it to [@easyctf](//twitter.com/easyctf)!


-------------------------------------

iSpy - 120 points
----------------
We intercepted some suspicious network activity. We think that the enemy has been exchanging important data. Can you help us figure out what it is? You can find a copy of the file [here](https://www.easyctf.com/static/problems/ispy/ispy.pcapng)

**Hint**:
You're going to need to be able to open that file. Something like [Wireshark](https://www.wireshark.org/) might help.

Here, again, we're given a `.pcapng` file. Opening it using `Wireshark`, and selecting 'Follow TCP Stream' reveals the HTTP reqeust being made. Where, in the end, the user is redirected to a page using `meta` tag as;
```
<meta http-equiv='refresh' content='0;url=http://postimg.org/gallery/2p8cfi4l2/49324a00/'>
```
I opened it up, and it's there; The flag.

Flag: `easyctf{pcap_fun!??}`

----------------------------

49 Shades of Gray - 125 points
----------------------------
We only have 49 shades of gray D:

#000000 to #F5F5F5... there's one shade missing! Find the hex value of the missing shade. Pound sign optional.

[Image](https://www.easyctf.com/static/problems/49-shades/shades.png)

**Hint**:
How can we tell which color is which?


-----------------------------------------

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

---------------------------------

sayonara - 325 points
---------------------
Found some interesting words of advice left by sayonara-bye... help me understand it!

[sayonara.mp3](https://www.easyctf.com/static/problems/sayonara/sayonara.mp3) MD5: 9f44501f0ac360c3255548c96b70aecb

**Hint**:
Why does that right channel sound strange?

