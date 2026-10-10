---
title: HOME LABBING PART1
date: 2026-10-10
categories: [HOME LABBING]
tags: [failure,brainf*ck]     
---

# INTRO 

this blog is me ranting about the absolute failure that was my first attempt at building a home server . It started one day when I got my hands on an HP laptop with these specs:

- | specs | 
| -------------- |
| 32gb RAM DDR5 | 
| 1TB SSD  |
| Intel Core 7 150U| 

# Tutorial I'm following 

So i picked up a proxmox youtube (creds : [yt video](https://youtu.be/k4MfN0SJa4Y?si=dXrR6IePeyuJVvj5)) Tutorial and started . With all excitement and enthusiasm , past-me had no idea what's coming

![poor happy guy](/assets/img/home-lab-part-1/20261007_114712.jpg){: .shadow, .rounded-10}


# THE BIG PROBLEM AND THE BIG IDEA 

going into this i knew that proxmox is built for servers and one of the special things about servers is that they don't come with wifi adapters . So proxmox does not come with wifi drivers installed .the HP laptop does not  have an ethernet port . Smart-past-me thought that won't be a problem . proxmox is debian based -> debian is linux -> linux is freedom . So i will istalll wifi drivers and problem solved 

![all is good](/assets/meme/cat-thumbs-up.jpg) {: .shadow, .rounded-10}

## The big failure part one 

I asked Gemini for its guidance and it suggested that i get my hands on the wpasupplicant debian package . it seemed convinced that I'd find said package in the proxmox ISO . so i went on searching i mounted the iso and kept looking for it (thanks to mount's loop device ) . after wrestling with directories that gemini is convinced they exist but they don't . I got lost for half an hour before deciding to just use the find command .....yeah should've done that first.

![poor me](/assets/img/home-lab-part-1/20261007_121357.jpg)

## The big idea part two

### USB Tethering

They say the simplest solution is often the correct one . so I went with USB Tethering .But alas ! proxmox makes use of something called linux bridges (i don't really understand that) , but what i understood is that there's a default network interface and default ip route table that should'nt be touched but i have to . So i deleted both of them and only kept the one from usb tethering.
ping worked so i tried apt-get update . And a NEW ERROR Appeared . apt tried accessing enterprise.proxmox.com so i disabled that . AND IT STILL FAILED MISERABLY !!!!!!!!!!!!!!!!!!!!!!!

![last straw](/assets/img/home-lab-part-1/20261007_123143.jpg)

## Conclusion ?

I went back to solving htb machines and I'll go look for a USB-Ethernet Adapter ...
