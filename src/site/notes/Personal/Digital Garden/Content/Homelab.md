---
{"dg-publish":true,"permalink":"/personal/digital-garden/content/homelab/","created":"2023-11-14T08:05:30.894-05:00"}
---

On February 16th, 2012 I opened my Plex account and started to host my own media. Over the course of the next 8 year, multiple copywrite infringement notices later, my interest in operating my own server within my home continued to grow. 

Since the early 2000's, I've always had an interest in linux and the open source software scene, but my background and interests didn't align deeply enough to really engage in the difficult to manage software that was available at the time. Eventually though, I found my way toward [[TrueNas\|TrueNas]], which was "FreeNas" at the time. This stand-alone operating system was perfect for someone with minimal skills to follow some online tutorials and get going in the home server space. Having jails within the platform allowed for easy containerization of applications and ensured the security of the operating system when I inevitably messed something up. 

For years, I ran an old desktop computer as my Plex server and manually uploaded files to the share NAS drives. During the pandemic, I even used it to host a [[Personal/Digital Garden/Content/Minecraft\|Minecraft]] server for a brief while until I realized that my dodgy internet connection and frequent power issues in my home made for a frustrating shared server experience. I eventually moved the server over to a dedicated hosting provider, but the bug was set and off I went. 

With the release of TrueNas Scale, a [[Kubernetes\|Kubernetes]] based version of TrueNas, it became that much easier to access a catalog of available applications and start down the rabbit hole of a true homelab. Spurned on by the folks over on reddit in the /r/homelab subreddit, I quickly walked through the [trash guide](https://trash-guides.info/) and was able to get the entire Aars suite up and running over the course of a weekend. 

I continue to leverage the homelab for learning, experimenting, and generally as a playground where I can create digital experiences for myself and my family. With the rise of easy to use tunneling from [[Cloudflare Tunnels\|Cloudflare Tunnels]] it became that much easier and secure to enable external access to my content, enabling me to share my server and various applications with family members, which is frankly, one of the most fun things that I get to do. 

I have personally found a lot of [[Personal/Digital Garden/Content/Value of Creation\|Value of Creation]] and self-fulfillment when I am able to make things and share them with others. Be it [[pottery\|pottery]], a homelab, or [[knitting\|knitting]]. It's a weird set of examples, I know, but it all revolves around the creation of shared experiences, and to me, that's a tremendously fulfilling experience and one that I don't get from playing [[video games\|video games]] or watching Netflix. 

Useful Links: 
[[Personal/Digital Garden/Content/Truenas Scale - Automated App Updates\|Truenas Scale - Automated App Updates]]
[[Personal/Homelab/TrueNas Scale Pool Migration\|TrueNas Scale Pool Migration]]
[[Personal/Homelab/Plex Meta Manager Install Guide\|Plex Meta Manager Install Guide]]
[[Personal/Homelab/Text to Speech\|Text to Speech]]
[[Personal/Homelab/Backblaze Backup Network Drive\|Backblaze Backup Network Drive]] - (Never got this working correctly)
[[Personal/Homelab/Paperless Management\|Paperless Management]]

- [ ] #homelab Create diagram of current-state homelab
- [ ] #homelab Figure out replacement B2 Cloud Backup approach
