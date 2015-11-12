Web
-----

Plot Twist - 20 points 
----------
We need to get the flag at [this](https://www.easyctf.com/static/problems/plot-twist/index.html) site. That shouldn't be too hard.

**Hint**:
There must be a backup on that site SOMEWHERE . . . you just have to look harder

This also presents nothing, but a static HTML page. I viewed its source code, and found nothing, because I didn't go through scripts. But when I checked **Scripts** using developer tools, I found the flag, it was printing it in the `console`.

Flag: `easyctf{remember_to_check_everywhere}`

----------

Teach Me How to Write Like This - 30 points 
---------
My friend Michelle found this cool new site, but you have to pay to read and she doesn't have money. Can you help her read the [fics](https://www.easyctf.com/static/problems/fandoms/index.html) anyways?

**Hint**:
Where can you find out what files are in a server?

It only required to view source code. If you really want to read the contents, you could delete `class='pay'` and `class='blur'`.

Flag: `easyctf{geico_geck0s}`

-------------------

2147483648% Secure - 35 points 
-----------
Hack my friend's [website](https://www.easyctf.com/static/problems/intro-js/index.html)! From what she tells me, it's super secure. Why don't we prove her wrong :)

**Hint**:
Don't try to figure out what the messy JavaScript code means. [Developer tools](https://www.google.com/search?q=developer+tools) help a lot in things like this.

The page, here, says 'A flag is hidden somewhere on this page; try to figure out what it is!'. I viewed the source code, and found the flag was written like;
```
var _0xa107=["\x64\x65\x76\x65\x6C\x6F\x70\x65\x72\x5F\x63\x6F\x6E\x73\x6F\x6C\x65\x5F\x69\x73\x5F\x79\x6F\x75\x72\x5F\x66\x72\x69\x65\x6E\x64","\x65\x61\x73\x79\x63\x74\x66\x7B","\x7D"];
			var _0x6fdc=[_0xa107[0],_0xa107[1],_0xa107[2]];
			var secret=_0x6fdc[0];
			secret=_0x6fdc[1]+secret+_0x6fdc[2];
```
Though I deobfuscated it to figure out the flag, we don't need to. As the `flag` says, developer `console` is our friend. Just type in `secret` and hit Enter, it will print the flag :) (`secret` is a variable name)

Flag: `easyctf{developer_console_is_your_friend}`

--------------------

Wastebin 1 - 90 points
---------
I created a paste-sharing site the other day. Since client-side is faster, I decided to retrieve the entire database and store it client-side. No one should be able to see it, right? Prove me wrong by finding the admin password. [page](https://www.easyctf.com/static/problems/wastebin-1/index.html)

**Hint**:
What's wrong with storing things on the client's browser?

This was amongst the easient one. The question says it all, the entire database is stored client side. I just viewed the source code, and found everyone's password, but we only needed admin's password ;)

Flag: `easyctf{cr4zy_p4ssw0rds}`

--------------------

Easter - 100 points
------
[page](https://www.easyctf.com/static/problems/easter/easter.html)

**Hint**:
Just look around.

It was hard, until I figured out that `console` can be used to deobfuscate JavaScript codes. The page contains nothing, except a picture. I viewed it's source code, and found some obfuscated JavaScript codes. I also tried deobfuscating them, but nothing helped. A friend in IRC told me that we could use `console` to do so. I copied the obfuscated JavaScript code, and printed it under `console`, which give me the deobfuscated JavaScript code, as shown;
<img src='http://i.imgur.com/C9WUd4D.png?1' />
The JavaScript code was adding an event listener, which when fired up would print the binary number;<br/>
`01111011011011010110100101110011011100110110100101101111011011100111001101110101011000110110001101100101011100110111001101111101`<br/>
Now, I only needed to convert it to ASCII.

Flag: `easyctf{missionsuccess}`

---------------

Personal Home Page - 225 points 
-----------------
[I hate PHP.](http://web.easyctf.com:10200/)

**Hint**:
You might not have permission to read the file, but someone else does ;)

The site cleary tells us that "**Instead of serving pages normally, all the pages are fetched with PHP before written to the screen!**", and that the flags are hidden under `/supersecretflag.txt`. A quick glance makes it all clear. The URLs are like;<br/>
`http://web.easyctf.com:10200/?page=pages/index.html`,<br/>
and, since pages are fetched before written to the screen, with PHP, it might be vulnerable to Local File Inclusion (LFI). I passed the parameter as `?page=supersecretflag.txt`, and it threw me the contents of `supersecretflag.txt`.

Flag: `easyctf{file_get_contents_is_9_safe} `

---------------------

Super Secure Lemons - 225 points 
------------
This [site](https://web.easyctf.com:10202/) uses an encryption technology to keep its lemons super secure! On second thought, it might not be as secure as we thought.

**Hint**:
Why is your browser giving you that funny security message?

The site, upon visiting, gave me a security warning. And, as the question relates to encryption technology, I immediately thought of viewing its certificate. And, there it was, quite easy ;)

Flag: `easyctf{never_trust_se1f_signd_certificates}`

----------------------

Wastebin 2 - 250 points
----------
So after the previous fiasco, I decided to generate a random `admin` password, and hide it in a file that no one will ever find. And don't try Googling it either, cuz Google can't find it either! Hahaha >:) [Link](http://web.easyctf.com:10207/2/index.php)

**Hint**:
Where can you find out what files are in a server?

Flag: `easyctf{looks_like_my_robot_proof_protection_isn't_very_human_proof}`

----------------------

Pretty Horrible Programming - 275 points
------------------
[I still hate PHP.](http://web.easyctf.com:10201/)

**Hint**:
How is the webpage checking your password?

The given site contains only a text field (`type='password'`), which takes password as input and sends `GET` request to itself. I viewed its source code (View Source), and found that its `php` source code is located at `index.source.php`. I viewed its `php` source code, and found that it was comparing passwords using `strcmp`, like;
```
$auth = false;
            if (isset($_GET["password"])) {
                if (strcmp($_GET["password"], $pass) == 0) {
                    $auth = true;
                }
            }
```
A quick Google Search gave me the idea that supplying an array, instead of a single parameter, results in comparision being `true`. 
The final request was;<br/>
`http://web.easyctf.com:10201/index.php?password[]=x`

Flag: `easyctf{never_trust_strcmp}`

--------------------

Wastebin 3 - 325 points
-----------------------
Hey I just learned this thing called MySQL! My admin account should be safe now! [Link](http://web.easyctf.com:10207/3/)

**Hint**:
What is [SQL](http://www.w3schools.com/sql/)

Upon reading the question given, I had no doubt that the site was vulnerable to SQL Injection. I opened the link, and checked for SQL Injection, entering;<br/>
`admin' or 'x'='x -- `<br/>
as `username`, and it revealed the flag it was hiding.

Flag: `easyctf{54771309-67e5-4704-8743-6981a40b}`

We could also read the `php` source code at `/index.source.php`, which is commented under source code (View Source).

------------------------

Infinity Star - 375 points
-----------------
Infinity Star Bank's [new website](http://web.easyctf.com:10206/) is up! In honor of their opening, they are offering a premium service that allows you to view flags.

Important note: the account `michael` is an admin account.

**Hint**:
If the transfer money feature is still under testing, who do you think can use it?

This actually took me more than a day, I guess. Idk why it didn't work out with BurpSuite, else I had solved it earlier. In order to get the flag, you need to register & buy their service worth $99.99. However, when you register, you get no money :P. There's a fund transfer page, from where you can transfer money to other users. Sadly, it says, '**You're not allowed to send transfers (feature under testing)**'. The fund transfer request, however, is a `GET` request. For example, if I want to transfer $100 to `canary`, it would be;<br/>
`http://web.easyctf.com:10206/api/bank/transfer?amount=1000&recipient=canary`<br/>
There's where it begins, the hint says 'who do you think can use it', and, of course, only admins can do it. There's a link, at the bottom, that says 'Report a Problem'. When you click, it says, "**Select which page you're having trouble with and an administrator will review it for you.**", and gives us a dropdown menu to select page we want to report. If you read it carefully, you might get it. It says, 'an administrator will review it for you'. That's it. You can send fund transfer link, and an administrator will click it to review, and voila. It's a simple `CSRF`. We now have money, let's view the flag ;)

Flag: `easyctf{csrf_protection_would_probably_have_been_a_good_idea_:/}`

----------------------

Borkened - 400 points
---------------------
There's a team that's breaking the rules and hiding flags on this site! Find the flag.

**Hint**:
The flag is on this site.

The hint says it all. The flag was on the site, and as the question says, **a team** is hiding the flag. It went easy for me, because I solved it before they added Cloudflare DDoS protection. I was using BurpSuite, and since it logs every requests & responses, I searched for team profiles using a pattern like;
`\/team\?.*?`.
There, I found `EasyCTF Team`'s profile commented, as shown;
<img src='http://i.imgur.com/sim79D1.png?1' />
I, then, requested `/team?EasyCTF`, and again searched for flag patterns like;
`easyctf\{.*?\}`.

Flag: `easyctf{h4xxing_th3_c0mpetition_s1t3}`

Here's a screenshot, I grabbed later;
<img src='http://i.imgur.com/z4l0wQ2.png?1' />
