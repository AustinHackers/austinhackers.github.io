---
layout: post
meetingid: "2014-05-29-0x005c"
author: jgor
speakernotes: true
---

[jgor](https://twitter.com/indiecom) discussed [known](http://www.openpcd.org/HID_iClass_demystified) [methods](http://proxclone.com/iClass.html) of attacking the HID iCLASS encrypted rfid card access system and demo'd tools he built including extracting the global HID standard DES authentication key and 3DES encryption keys from a reader, extracting the last swiped card from a reader, cloning / creating iCLASS cards with arbitrary credentials, and sniffing the wiegand interface to steal card credentials and pins. Demo [gear](https://pbs.twimg.com/media/Bo0_MZFIMAAoGBX.jpg:orig), arduino-based controller [code](https://github.com/jgor/wiegand-controller), wireless wiegand in-line skimmer [code](https://github.com/jgor/wiegand-skimmer), [video](https://www.youtube.com/watch?v=daPb3_X3KP0) of the skimmer in action.

