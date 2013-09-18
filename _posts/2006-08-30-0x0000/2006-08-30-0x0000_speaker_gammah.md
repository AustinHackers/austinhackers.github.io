---
layout: meeting
meetingid: "2006-08-30-0x0000"
author: Gammah
speakernotes: true
---

I did a quick demo of the insecurity in certain VOIP handsets, which
download their configuration from an Asterisk server in the clear. This
allowed me to observe the authentication settings for a number of phones
in my office, and to spoof each extension. The demo consisted of a
one-line shell script that iterated thru each phone extension, and I
then called each extension in turn, causing my VOIP phone (laptop) to
ring as the spoofed extension.

