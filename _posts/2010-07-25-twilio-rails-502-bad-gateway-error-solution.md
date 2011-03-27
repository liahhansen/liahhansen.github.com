---
layout: post
title: Twilio & Rails - 502 Bad Gateway Error Solution
---
{{ page.title }}
================


I ran into an issue while writing a Twilio app in Rails where Twilio kept getting a 502 bad gateway error.  The url I was using was definitely working, so that wasn't the issue.  I did a little google sleuthing and the answer is putting the following code into the controller:

{% highlight ruby %}
skip_before_filter :verify_authenticity_token
{% endhighlight %}

