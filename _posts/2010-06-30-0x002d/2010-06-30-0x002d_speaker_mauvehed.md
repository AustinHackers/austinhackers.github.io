---
layout: meeting
meetingid: "2010-06-30-0x002d"
author: mauvehed
speakernotes: true
---

This month I spoke about the Diablo 2 saved game file checksum. This
checksum is used to protect the saved character file that stores all of
our game information such as completed quests and also character info
like level, money, items, etc. Before you can modify the file you'll
have to be able to compute the final checksum. The following is initial
PoC work I did in preparation for future D2 projects and eventual D3
work.

* d2checksum initial write up: [http://mhlabs.nullbyte.net/2010/04/understanding-diablo-2-file-checksum.html](http://mhlabs.nullbyte.net/2010/04/understanding-diablo-2-file-checksum.html)
* d2checksum rewrite in python: [http://mhlabs.nullbyte.net/2010/06/understanding-diablo-2-file-checksum-in.html](http://mhlabs.nullbyte.net/2010/06/understanding-diablo-2-file-checksum-in.html)
* Google code: [http://code.google.com/p/mhlabs/source/browse/trunk/d2checksum/d2checksum.py](http://code.google.com/p/mhlabs/source/browse/trunk/d2checksum/d2checksum.py)

