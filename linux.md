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
And, there it was :)<br/>
Flag: `easyctf{w0aw_stor1ng_fl4gs_in_pla1nt3xt_i5_s0oper_s3cure}`

--------------------

Hijacked! - 100 points
-----------
Someone planted a file on our computer (the [shell server](//easyctf.com/shell)), but we don't know what it is! The only clue that we have is that it's owned by a user called `l33t_haxx0r`. Can you figure out the flag?

**Hint**:
Try to look up useful Linux commands.

The question only gives us the clue that the file is owned by `l33t_haxx0r`. Which, still, is enought to find a file. Linux provides us with a very useful command line utility that can find files based on different attributes, `find`. I only fired up the command, and found the file.
```
$find / -user l33t_haxx0r 2> /dev/null 
/var/www/html/index.html
```
I tried to find the flag using `grep` like;
```
$grep 'easyctf' /var/www/html/index.html
```
But it didn't return any matches. I, then, opened the file using `vim`, and scrolled through the pages. There, I found the flag. `grep` didn't return any matches, because it wasn't in a single line.

Flag: `easyctf{c0mp1et3ly_r3kt}`

---------------------------

Same Difference - 125 points
-------------------
We've noticed that a list of passwords has been modified. Compare the original `master_copy.txt` to the `suspicious.txt` and tell us what the password was changed to! The files are on the shell server at `/problems/same_difference`.

This can be solved only with the tools available in the shell. No scripting languages are required.

**Hint**:
There's a pretty cool Linux command called `diff` that might be useful for you.

This, as has been said in *hint*, can easily be solved using `diff`. The command I used is;
```
$diff --suppress-common-lines master_copy.txt suspicious.txt 
8834c8834
< easyctf{17c85a939e5ee1b0b0e00ed7187d11f7}
---
> easyctf{60a57b3974029aa012e66b05f122748b}
```

Flag: `easyctf{60a57b3974029aa012e66b05f122748b}`
