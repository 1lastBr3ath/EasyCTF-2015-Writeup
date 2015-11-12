Linux
-----

Now You See Me, Now You Don't - 75 points
--------------
Now you see me, now you don't? There's a file in `/problems/elusive`, but I can't seem to find it. Find it and print its contents!

**Hint**:<br/>
What are hidden files in Linux?

This was the easiest of all, I guess. I'm used to `ls -a`, and it was all that required. Doing so revealed a hidden file named `.hidden_file`. That was it, it contained the flag. It was even easier than **'Hello, world!'** program, IMO.

Flag: `easyctf{just_playing_h1de_and_seek_lel}`

-------------

Mrrow????? - 75 points
-------------
A lonely little text file wants to play a game: /problems/owner.

**Hint**:<br/>
Google is always your friend.

It was even easier. The question says nothing at all, but we'll find a file in that directory, `file.txt`, that reveals the format of flag, which is as `easyctf{<owner>:<group>}`.

Now, all we need to do is,
```
$ls -l file.txt
-rwxr-xr-x 1 leonidas sparta 165 Nov  4 01:04 file.txt
```
The flag, thus, becomes `easyctf{leonidas:sparta}`

------------

San Francisco Symphony - 75 points
-----------------
Who knew musicians could program? They put a flag inside `/problems/sfs/sfs`! But when I run the program, it's not printing out the flag. Find the flag!

**Hint**:<br/>
Darn. That c file isn't going to help much either. How can we find the flag using only the binary?

If you read the question carefully, it says '*They put a flag inside `/problems/sfs/sfs`! But when I run the program, it's not printing out the flag. Find the flag!*'. Though, I tried to run the program again :). Also, we couldn't read the source code, becase we didn't have **reading** permission, which left me no choice. Therefore, I tried reading `sfs` itself, and piped it through `grep` like
```
$strings sfs|grep easyctf
easyctf{w0aw_stor1ng_fl4gs_in_pla1nt3xt_i5_s0oper_s3cure}
```
And, there it was :)
Flag: `easyctf{w0aw_stor1ng_fl4gs_in_pla1nt3xt_i5_s0oper_s3cure}`

--------------------



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
find / -user l33t_haxx0r 2> /dev/null

