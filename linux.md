Linux
-----

A Picture is Worth a Thousand Words - 100 points
--------------

A picture is worth a thousand words. Can you find the (JPEG) picture among a thousand files? Connect to the EasyCTF SSH server and find the files in `/problems/1000words`. The files are also available for download [here](https://www.easyctf.com/static/problems/1000words/data.zip).

**Hint**:<br/>
Grep is always your friend.

Here, we were provided 1000+ files, each with random name, and with no file extension. We could also download the file from given link. I tried solving it by connecting to the SSH. It was easier to find the JPEG image, just tried;

```
$ file * | grep JPEG
UgeVjTlmZjNFvULk: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 266x71, frames 3
```

I found the image, however there were no flags in it. I tried reading its content using `cat` and `strings`, and they were of no help. Finally, I decided to download the file given in question, and opened the image. And, there it was.

Flag: `easyctf{it_must_be_pretty_hard_reading_this}`


Now You See Me, Now You Don't - 75 points
--------------
Now you see me, now you don't? There's a file in `/problems/elusive`, but I can't seem to find it. Find it and print its contents!

**Hint**:<br/>
What are hidden files in Linux?

This was the easiest of all, I guess. I'm used to `ls -a`, and it was all that required. Doing so revealed a hidden file named `.hidden_file`. That was it, it contained the flag. It was even easier than **'Hello, world!'** program, IMO.

Flag: `easyctf{just_playing_h1de_and_seek_lel}`
