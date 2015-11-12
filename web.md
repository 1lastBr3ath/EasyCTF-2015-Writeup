Web
-----

Wastebin 3 - 325 points
-----------------------
Hey I just learned this thing called MySQL! My admin account should be safe now! [Link](http://web.easyctf.com:10207/3/)

**Hint**:
What is [SQL](http://www.w3schools.com/sql/?

Upon reading the question given, I had no doubt that the site was vulnerable to SQL Injection. I opened the link, and checked for SQL Injection, entering;<br/>
`admin' -- `<br/>
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
