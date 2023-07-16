---
title: The NPC Manifesto #17
slug: the-npc-manifesto-17
date_published: 2023-04-30T21:23:05.000Z
date_updated: 2023-04-30T21:23:05.000Z
tags: Manifesto, Blog
---

Good Evening reader,

It's been fun to get the private server up and running. If you're new, I'm ghosting cloud platforms and creating a private virtual server. This will be the digital equivalent of getting off the grid:

- npcmanifesto.xyz is already registered as a web domain
- storage for the domain needs to be created
- SSH key should be created to have the domain encrypted
- Private virtual server in the same city as the SSH encrypted storage
- Attach the storage to the sever
- Point the domain to the server
- Configure the SSH into the root IP address of the server (can now remote into the server)
- Create username to access server
- Format storage
- Make sure the server is secured
- Nice simple website to host the letters I send to you
- Create contacts and host calendars on website
- Backups
- Receive mail from contacts
- Send mail to contacts

I've decided to redo the steps above by pointing the server to a brand-new domain. Our digital castle in the sky will have a name that is familiar to us:
![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-30-at-1.28.46-PM.png)
I've also created my user, which will point to *npcmanifesto.xyz*. The storage has also been encrypted in the server. I can now plug in 40GB storage by using the commands 'm' and disconnecting it with 'm-x':
![](__GHOST_URL__/content/images/2023/04/Screen-Shot-2023-04-30-at-4.19.46-PM.png)
If you've been following from letters [#15](__GHOST_URL__/blog/the-npc-manifesto-15/) and [#16](__GHOST_URL__/blog/the-npc-manifesto-16/), the next thing to do is format the storage to the OpenBSD OS.  These are the terminal commands that I used to encrypt my storage. The commands that I typed do not have ">>" (those are the server outputs):

    doas su
    disklabel -E sd1
    
    >>“Label editor (enter '?' for help at any prompt)”
    a a
    
    >>offset: [0]
    [enter]
    >>size: [83886080]
    [enter]
    
    >>FS type: [4.2BSD]
    RAID
    
    >>sd1>
    w
    >>sd1>
    q
    >>No label changes.
    bioctl -c C -l sd1a softraid0
    
    >>"New passphrase:"
    [Enter your password]
    >>"Re-type passphrase:"
    [Enter your password]
    
    >>“softraid0: CRYPTO volume attached as sd2”
    disklabel -E sd2
    
    >>“Label editor (enter '?' for help at any prompt)”
    a a
    
    >>“offset: [0]”
    [enter]
    >>size: [83886080]
    [enter]
    
    >>FS type: [4.2BSD]
    [enter]
    
    >>sd1>
    w
    >>sd1>
    q
    >>No label changes.
    newfs sd2a
    >>“/dev/rsd2a: 40959.7MB in 83885536 sectors of 512 bytes”
    

Voila, we now have encrypted storage attached to our server. The next few commands install a package to connect and disconnect from storage seamlessly. Think of it like being able to plug and remove a USB stick in a computer:

    pkg_add rsync--iconv
    exit
    mkdir bin
    cd bin
    echo '#!/bin/sh\ndoas bioctl -c C -l sd1a softraid0\ndoas mount        /dev/sd2a /mnt\nls -l /mnt' > m
    echo '#!/bin/sh\ndoas umount /mnt\ndoas bioctl -d sd2\necho "unmounted"' > m-x
    

With the script above, we can now access storage directly from the npcmanifesto server using 'm' and 'm-x'. My dear friend, I now see that having access to a private virtual server is like owning internet land. This can let us build digital castles in the sky. The manifesto is merely a blueprint to get there.

pura vida,
-rushil
