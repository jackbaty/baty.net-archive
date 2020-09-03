---
title: "Publishing a static blog with Zeit Now"
slug: "publishing-with-zeit-now"
date: "2017-11-14T12:22:01-04:00"
tags: ["blogging","static"]
draft: false
description: Using Zeit Now to publish my notes as a static site
---

I decided to use my Tinderbox-generated static blog as a real world test of https://zeit.co.

It was pretty simple. I started out with a folder full of HTML files generated by Tinderbox. Then...

1. Install [Zeit Desktop](https://zeit.co/download)
1. Run `now` from within the html folder
1. Done. The site is now available via an auto-generated URL like notes-xxxyyyzzz.zeit.sh

I'd of course rather use a nicer, more permanent URL so I did this...

1. Create a CNAME DNS record for notes.baty.net pointing at alias.zeit.co
1. Run `now alias notes-xxxyyyzzz.zeit.sh notes.baty.net`
1. Add the verification TXT DNS record

This made notes-xxxyyyzzz.zeit.sh available at notes.baty.net. Each time I deploy, the instance is available at a new, auto-generated URL. The nice thing about that is each deployment creates a new, permanent version of the site. It also means that the alias must be updated each time. To do that, I created a now.json file that looks like this...

```json
{
  "name": "notes",
  "alias": "notes.baty.net"
}
```
So to deploy any new changes, I export the Tinderbox document and type...

`now && now alias`

I've made this into a Tinderbox "Stamp" so that all I have to do is select "Publish" from the Stamps menu and it runs the commands for me.

This means the site is available, with automatically-configured SSL, at https://notes.baty.net/. Pretty cool.