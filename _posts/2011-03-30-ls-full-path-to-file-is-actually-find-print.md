---
layout: post
title: Unix - find /path_to_search -print | grep filename
---
{{ page.title }}
================

I was using <code>ls -R | grep filename</code> trying to find a particular file deep within the font bowls of Tex.  It found the file just fine, but then I needed to know where the file lives.  Here is the magic code: <code>$ find /path_to_search -print | grep filename</code>
