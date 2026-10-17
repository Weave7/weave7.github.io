--- 
title: 30-Days-Challenge Day 5 
date: 2026-10-17 
categories: [30 day challenge]
tags: [HackTheBox,brainf*ck]
--- 


# Solving POV 
Day 5 , medium windows . I was not expecting to spend so much time on trying to run ysoserial on linux but thanks to this guy [ar0x4](https://github.com/ar0x4/ysoserial.net-docker) i managed to run it (though i didn't like the script and opted to execute directly inside the container ) . I spent more time on that rabbit hole than I'd like to admit ( and I also made a mistake in the post request for the exploit which vacuumed an hour off my life away ... ) . Other than my stupidity I really enjoyed this machine . especially the Priv Esc part since i didn't like ippsec's way and absolutely hated the official walkthrough's solution so I went off trying my own luck with the shell shenanigans and finally got a meterpreter shell as the user alaading

![pwned](/assets/img/30-days-challenge/Day5/pwned.webp)


# Tomorrow's TombWatcher (medium windows)

I HAVE HIGH EXPECTATIONS ! 

after nmap , smb & web enumeration (both are empty) we move to bloodhound which quickly shows a clear but long attack-chain . It involves different AD TTPs (Tacktics Techniques & Procedures) which aligns perfectly with the goal of this whole challenge . To spice it up at the end it includes a unique enumeration step (finding soft deleted ADObjects ) then exploiting ESC15 , the first Scenario of which doesn't work because of SSL weird quirks 


the only problem is Tomorrow we (my university's CyberSec Club) are hosting a CTF Tomorrow that I have to administer let's hope i find the time to complete the challenge ( thinking to maybe solve it at 5 Am or switch the 2 parts ...)

Anyways,Day 5 wrapped up ! 
