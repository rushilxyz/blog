---
title: The NPC Manifesto #15
slug: the-npc-manifesto-15
date_published: 2023-04-29T22:48:12.000Z
date_updated: 2023-04-29T22:48:12.000Z
tags: Blog, Manifesto
---

Good Evening reader,

In my last [letter](__GHOST_URL__/blog/the-npc-manifesto-14/) to you, I outlined the steps to go off the grid from cloud platforms. Let us not be dependent on any particular company or software to communicate. Only then, will this manifesto have a lindy existence, with evergreen internet life. I will show you how.

Internet platforms are like music labels that own the masters of an artist. Many creators get screwed over because they don't own the music they create. Of course, there are monetary reasons why an artist will sign with a label. Yet, we must remember that wealth is not a number. It's merely the transformations that you are capable of bringing about. 

These are the basics to go off the grid from company clouds:

## Domain

[www.rushil.xyz](www.rushil.xyz) is the domain used to host the letters that I send to you

## Storage

I won't be using an on-premise server or local hard-drive, but will deploy a private virtual server through [Vultr.com](vultr.com). I've set up a block storage (HDD) of 40GB/dollar, which should be enough for our current experiment.

## Secure Shell

The server must have SSH encryption, meaning an SSH key must be created from your local computer. This will allow us to remote into the server. If you need help creating an SSH key, you can [email](mailto:xyzrushil@gmail.com) me or ask gpt. 

I used the following commands on my mac terminal:

- ssh-keygen -t ed25519
- Enter file in which to save the key (/Users/yourname/.ssh/id_ed25519):
- It prompts for passphrase so keep it empty for now and press enter
- The key is created in a file called id_ed25519.pub
- Locate id_ed25519.pub and open it as a text file
- The SSH key should be similar to this:

    ssh-ed25519 AAAAC3NzaC1XO5iclCcrHbGRPoj4LUpqa2baqYQRmCZ1+NV4sBDr you@computer
    

Configure that SSH key into the server instance before deploying the server.

## Server

The server will have the following instance:

- Cloud compute virtual machine (for low-traffic websites)
- Regular Intel CPU and SSD performance
- OpenBSD operating system (7.3 x64)
- 25 GB SSD for 1vCPU

## Connecting The Dots

My friend, we've laid the foundation to build our digital castle on the sky. The next letter will explain how to:

- Attach storage to the server
- Point domain to the server
- SSH remote into the server root
- Create a username for root access 

Yes, this is still considered the so-called cloud, but it limits the constraints of personal data companies can control. I don't want to get into reasons why I'm going off the digital grid just yet. I'd rather have it done before explaining.

pura vida,
-rushil
