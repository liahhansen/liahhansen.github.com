---
layout: post
title: Push to Heroku from a Branch of Your Local Git Repository
---
{{ page.title }}
================

We spent some time searching for a bit of git hocus pocus to solve this one...here's the spell:

<code>git push heroku <branch_name>:master</code>

Our situation:
 
1. A production server
2. A staging server
3. A sandbox server

We have a branch in our git repo for the sandbox server & needed to be able to push straight from that, not from master.  The little colon did the trick!

A couple resources:

* [http://www.mail-archive.com/heroku@googlegroups.com/msg04039.html](http://www.mail-archive.com/heroku@googlegroups.com/msg04039.html)
* [http://suitmymind.com/blog/2009/06/02/deploying-multiple-environments-on-heroku-while-still-hosting-code-on-github/](http://suitmymind.com/blog/2009/06/02/deploying-multiple-environments-on-heroku-while-still-hosting-code-on-github/)

