--- 
title: 30-Days-Challenge Day 1
date: 2026-10-13
categories: [30 day challenge]
tags: [HackTheBox,brainf*ck]
--- 

# Part 1 : Pwning a machine 
## quick writeup to check if my understanding is solid
today's machine is fluffy , which is an easy rated windows box that is by no means easy . credits to this guy's great writeup on [medium](https://medium.com/@ivandano77/fluffy-writeup-hackthebox-easy-machine-f5d460be3312) 
The box takes you through these steps :
As is common in real life Windows pentests, you will start the Fluffy box with credentials for the following account: j.fleischman / J0elTHEM4n1990! 
it starts by an nmap scan that shows the usual domain controller's services running (DNS , Kerberos , LDAP ... and SMB) 
enumerating services using enum4linux doesn't show anything interesting , neither does user enumeration do us any good 
we quickly run bloodhound in the background and check smb shares with our credits . We find a pdf that has a report about critical CVES , the second of which catches the eye : CVE-2025-24071 . a vulnerability in File explorer . The big idea is that when a user unzips an archive , if said archive contains a .library-ms file it initiates an NTLM authentication over the networks which allows for LLMNR poisoning 
to exploit it we just upload the malicious zip to the IT share that we have write access to . start responder and then wait to capture an NTLM hash 
We then get p.agile's hash that's then cracked and we get plain text password . Checking with bloodhound for shortest path from owned to tier zero , we see an interesting path . Exploiting GenericAll(simply adding our user to the group) and then GenericWrite (shadow credentials attack) we get our hands on winrm_svc service account's hash ---> user flag (pass-the-hash).
going back to bloodhound again we see that we can do the same attack to ca_svc certificate service account , so we do just that 
using certipy to check for templates we find that there's a vulnerable ESC16 template that allows us to fake user principal name and the request the NTLM hash of the administrator account ---> pwned 

[pwned](/assets/img/30-days-challenge/Day1/pwned.png)

## Conclusion

My understanding of Active Directory Certificate Services is lacking . I may choose to unlock the tier 3 HTB module 'AD CS Attacks' for 500 cubes , but not now since i plan to go through the theory behind these boxes after the 30 day challenge and there's still Game Of Active Directory that I plan on hosting in my Home Lab

# Part 2 : Tomorrow's lab 

Tomorrow's lab is Jeeves (the second box in the CPTS prep track) . It's a medium windows , the initial foothold is very simple (an exposed web endpoint of a jenkins instance that allows anonymous access) the priv esc can either be the unintended SeImpersonatePrivilige that can be exploited with the Potato Family or cracking a KeePass database that has the administrator's hash .
The only thing special about this box is that there is no root.txt file in the administrator's desktop but we find a hmm.txt and an alternate data stream for said file that takes us to root.txt ( which was a novel concept to me so that's cool).
Anyways thanks to ippsec and 0xdf for their writeups and amazing concept .

Day 1 wrapped up ! 
