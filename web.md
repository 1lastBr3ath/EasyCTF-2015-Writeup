Web
-----

Borkened - 400 points
---------------------
There's a team that's breaking the rules and hiding flags on this site! Find the flag.

**Hint**:
The flag is on this site.

The hint says it all. The flag was on the site, and as the question says, **a team** is hiding the flag. It went easy for me, because I solved it before they added Cloudflare DDoS protection. I was using BurpSuite, and since it logs every requests & responses, I searched for team profiles using a pattern like;
`href=\"\/team\?.*?\"`.
There, I found `EasyCTF Team`'s profile commented, as shown;
<img src='http://i.imgur.com/sim79D1.png?1' />
I, then, requested `/team?EasyCTF`, and again searched for flag patterns like;
`easyctf\{.*?\}`.

Flag: `easyctf{h4xxing_th3_c0mpetition_s1t3}`

Here's a screenshot, I grabbed later;
<img src='http://i.imgur.com/z4l0wQ2.png?1' />
