---
title: The NPC Manifesto #16
slug: the-npc-manifesto-16
date_published: 2023-04-30T04:39:48.000Z
date_updated: 2023-04-30T21:33:07.000Z
tags: Blog, Manifesto
---

Good Evening reader,

The frequency of the letters have been increasing at the pace that I work . Otherwise, the todos from the [last letter](__GHOST_URL__/blog/the-npc-manifesto-15/) will never get done. PSA: the website that the current manifesto is resting on is: [https://rushil.ghost.io](__GHOST_URL__/). I'll be ghosting that platform soon enough.

Instead, we'll be using the *rushil.xyz* domain for our off the grid castle in the sky.

So far, I've attached the encrypted storage to the server.
![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-29-at-9.47.53-PM.png)
The domain still needs some figuring out, but I'm glad to be using an OS with a blowfish on it:
![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-29-at-11.46.36-PM.png)
As the public relations rep for the [president of Vaughan Aquatic Studies](https://www.youtube.com/watch?v=zqFTwZbe-ig), I approve the OpenBSD Operating System. My friend, after the last letter I sent to you, few hours have gone to figuring out the [OpenBSD OS](https://www.openbsd.org/goals.html). 

I have accessed the server and created a username to remote from my local mac. The commands below shows the steps I did to create a username and password. 

Assuming you're in a new mac terminal:

    ssh root@YOUR-IP-ADDRESS
    

![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-29-at-10.39.06-PM.png)
Once you've hacked the mainframe of your server, you can do a *syspatch* to get latest updates, then *reboot*.
![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-29-at-10.45.01-PM.png)
Once rebooted, I created my user.
![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-29-at-11.03.23-PM.png)
Once my user got created, these commands gave root access to the server from my local mac using the SSH key we created in the [last letter](__GHOST_URL__/blog/the-npc-manifesto-15/):

    cp /root/.ssh/authorized_keys /home/yourusername/.ssh/
        
    echo "permit nopass yourusername" > /etc/doas.conf
    
    sed -i 's/RootLogin yes/RootLogin no/g' /etc/ssh/sshd_config
    
    echo 'PasswordAuthentication no' >> /etc/ssh/sshd_config
    
    rcctl restart sshd
    

I now have access to a server with capabilities for developers. 

It will be like driving a formula 1 car, when all I've known is Toyota. 

My friend, I apologize for the high frequency of letters, but it's fun to capture this in real time as it's happening. Understanding complex systems are worth knowing.

pura vida,
-rushil
