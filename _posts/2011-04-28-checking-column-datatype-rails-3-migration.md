---
layout: post
title: Checking A Column's Datatype in a Rails 3 Migration
---
{{ page.title }}
================

The answer:
{% highlight ruby %}
Widget.columns_hash["id"].sql_type
{% endhighlight  %}


