---
layout: post
meetingid: "2007-08-29-0x000b"
author: I)ruid
speakernotes: true
---

I spoke about context-keyed payload encoding. I'm not making my slides
available this time since I'm submitting this as my talk for ToorCon 9,
but you can read the abstract for the paper if you like:

Abstract: A common goal of payload encoders is to evade a third-party
detection mechanism which is actively observing the attack traffic
somewhere along the route from an attacker to target application,
filtering on commonly used payload instructions. More often than not,
however, payload encoders are easily detected themselves and either
decoded or blocked. Even so-called keyed encoders utilize easily
observable, recoverable, or guessable key values in their encoding
algorithm, thus making decoding on-the-fly trivial once the encoding
algorithm is identified. It is feasible that an active observer may
exploit the inherent functionality of the decoder stub to decode a
suspected exploit's payload in a sandbox environment in order to inspect
the contents of that payload and make a control decision about the
traffic. This paper presents a new method of keying an encoder which is
based entirely on contextual information which is predictable or known
about the target by the attacker and constructable or recoverable by the
decoder stub when executed at the target. An active observer of the
attack traffic, however, should be unable to decode the payload due to
lack of the contextual keying information.

I also mentioned an auxiliary tool that I wrote for this research called
smem-map. You can grab it at it's sourceforge project page:

[http://sourceforge.net/projects/smem-map/](http://sourceforge.net/projects/smem-map/)

