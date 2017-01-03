---
date: 2014-02-27 18:00:00
layout: post
meetingid: "2014-02-27-0x0059"
author: zxcvbnm
speakernotes: true
---

What does an IRC botnet want with my server?

I see PHP-CGI injection attacks against our web servers on a daily basis. Usually I just pull down the file they are attempting to run and look at the code. Every now and then I'll join the IRC server and watch.

I did the usual investigation and watched the numbers rise. This botnet was averaging 60 compromised hosts per hour. I thought that was pretty good. 

So, I spun up a server as a honeypot and started capturing data.

We'll do a quick drive-by look at their:
1) Method of initial infection
2) Getting a foothold
3) Profiling and organizing the bots
4) Tasks of the botnet
