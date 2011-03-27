---
layout: post
title: Bundle Config & Bundle Open
---
{{ page.title }}
================

I wanted to be able to open up gems easily from the command line.  I tried 

{% highlight bash %} 
bundle open unicorn 
{% endhighlight %} 

and got the following error:

To open a bundled gem, set $EDITOR or $BUNDLER_EDITOR

To get rid of this error I added the following to .profile: 
{% highlight bash %} 
export BUNDLER_EDITOR=mate
{% endhighlight %}

This causes TextMate to open the gem of choice when I call: 
{% highlight bash %} 
bundle open unicorn 
{% endhighlight %}
