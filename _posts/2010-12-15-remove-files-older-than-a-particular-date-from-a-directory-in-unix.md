---
layout: post
title: Remove Files Older Than a Particular Date From a Directory in Unix
---
{{ page.title }}
================

I have a folder filled with hundreds of images.  Most of the images were first added to the folder on May 19th.  The folder I'm moving them to already has all the images that were added on May 19th, so to save time, I don't want to move the May 19th images. I made a back up of my images folder that and am using the below commands within it. I only want to keep images added after May 19th in the folder so that I can zip them up and move them to another server.  I'm using a dummy folder I made locally to test this out.  Here are the unix commands I will use:

<br /><br />

{% highlight bash %}
[Liah-Hansens-MacBook-Pro:~/test]$ ls -al
total 0
drwxr-xr-x   6 liahhansen  staff   204 Dec 15 15:01 ./
drwxr-xr-x+ 75 liahhansen  staff  2550 Dec 14 19:18 ../
-rw-r--r--   1 liahhansen  staff     0 Dec 15 13:58 goodbye
drwxr-xr-x   2 liahhansen  staff    68 Dec 14 19:30 happy/
-rw-r--r--   1 liahhansen  staff     0 Dec 15 13:58 hello
-rw-r--r--   1 liahhansen  staff     0 May 24  2010 timefilealittleolder
[Liah-Hansens-MacBook-Pro:~/test]$ touch -am 05192010 timefile

[Liah-Hansens-MacBook-Pro:~/xargs_test]$ ls -al
total 0
drwxr-xr-x   7 liahhansen  staff   238 Dec 15 15:11 ./
drwxr-xr-x+ 75 liahhansen  staff  2550 Dec 14 19:18 ../
-rw-r--r--   1 liahhansen  staff     0 Dec 15 13:58 goodbye
drwxr-xr-x   2 liahhansen  staff    68 Dec 14 19:30 happy/
-rw-r--r--   1 liahhansen  staff     0 Dec 15 13:58 hello
-rw-r--r--   1 liahhansen  staff     0 May 19  2010 timefile
-rw-r--r--   1 liahhansen  staff     0 May 24  2010 timefilealittleolder
{% endhighlight %}

**The important part:**

{% highlight bash %}
[Liah-Hansens-MacBook-Pro:~/test]$ find . -mtime +208 -type f | xargs rm
{% endhighlight %}

**Now timefile is gone.  Yay!**

{% highlight bash %}
[Liah-Hansens-MacBook-Pro:~/xargs_test]$ ls -al
total 0
drwxr-xr-x   6 liahhansen  staff   204 Dec 15 15:11 ./
drwxr-xr-x+ 75 liahhansen  staff  2550 Dec 14 19:18 ../
-rw-r--r--   1 liahhansen  staff     0 Dec 15 13:58 goodbye
drwxr-xr-x   2 liahhansen  staff    68 Dec 14 19:30 happy/
-rw-r--r--   1 liahhansen  staff     0 Dec 15 13:58 hello
-rw-r--r--   1 liahhansen  staff     0 May 24  2010 timefilealittleolder
{% endhighlight %}

**Yay!**

When I performed these commands on the real files, I ran into a problem where many of the file names had whitespace in them.  This caused rm to fail and I still had many files left in the folder from May 19th.  Here is the command that got rid of them once and for all:

{% highlight bash %} 
find . -mtime +208 -type f | xargs -I{} rm '{}'
{% endhighlight %}

Checking just to make sure:

{% highlight bash %} 
ls -al |grep "May 19" | wc -l
0
{% endhighlight %}

Golden!
