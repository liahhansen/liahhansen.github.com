---
layout: post
title: Checking A Column's Datatype in a Rails 3 Migration
---
{{ page.title }}
================
Today we were temporarily perplexed because Facebook ids were being
saved in MySQL as completely different numbers than we were expecting.
The problem ended up being that the datatype was Int instead of BigInt. 

We wanted to be able to determine the datatype of a column through
ActiveRecord in our migration.  This is how to get that info:

{% highlight ruby %}
Widget.columns_hash["id"].sql_type
{% endhighlight  %}


