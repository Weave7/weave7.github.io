--- 
title: 30-Days-Challenge Day 7 
date: 2026-10-19
categories: [30 day challenge]
tags: [HackTheBox,brainf*ck]
--- 


Considering that yesterday , I chose an easy machine to review i don't really have anything to say about administrator . this is day 7 so I'm starting to feel used to it 
# Pwning administrator (medium windows)

![pwned](/assets/img/30-days-challenge/Day7/pwned.webp)

yeah and also since administrator wasn't stimulating enough i went ahead and solved the seasonal machine (that's kinda misleading lol , i spent the last week making little progress everyday )

![pwned Stream](/assets/img/30-days-challenge/Day7/Stream.webp)

# OH LORD DID I BITE MORE THAN I CAN CHEW 

I got runner's high at the gym so when choosing the machine for tommorrow I overestimated how much brain juice I got left and thus I chose StreamIO (rated medium windows but at this point we all know HTB's rating are always off by a mile ) . Ippsec's video on it is 1:49:48 long , more than hard machines . It's a complex box that requires a mastering of techniques from manual SQL injection on an MSSQL server (having to deal with MSSQL's quirks and weirdness) . password spraying . LFI leading to information disclosure that you use to exploit RFI leading to Remote code execution , but you don't land as the user with the flag so lateral movement after another lateral movement and then some AD enumeration and exploitation .... yeah it's a mess (and of course Ippsec can still manage to add side quests among all of this)


![no juice left ](/assets/memes/no-brain-juice-left-cat.webp)

Anyways,Day 7 wrapped up ! 
