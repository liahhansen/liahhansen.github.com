---
layout: post
title: Let the Blogging Begin!
---
{{ page.title }}
================
UPDATE: As of March 2011 my blog has migrated from Radiant to Jekyll.

I've been attending some amazing Ruby & RoR workshops and classes for the last month.  The whole time I've been wanting to blog about all of my breakthroughs with programming.  One of my RoR extracurriculars has been an informal meeting of 12-15 newbies every Sunday from 1-5 in a cottage belonging to our RoR teacher, Alex Chaffee.  We've built a humble - very, very humble blog app.  I was hoping to get it ready for prime time sooner and use it for my personal blog.  After three weeks we finally implemented authentication, but it still lacks in many areas, so I thought I'd use Radiant in the meantime.  It took me all of 10 minutes to install Radiant!  It is simple - much more barebones than Wordpress or Drupal, but it gets the job done while giving me a chance to watch RoR in action.   Here are all 12 lines of commands it takes to install:

  1.  <code>radiant -d sqlite3 liah-hansen</code>   
  2.  <code>cd liah-hansen/</code>   
  3.  <code>rake db:bootstrap</code> 
  4.  <code>git init</code> 
  5.  <code>heroku create</code> 
  6.  <code>heroku addons:add custom_domains</code> 
  7.  <code>heroku domains:add liahhansen.com</code> 
  8.  <code>heroku domains:add www.liahhansen.com</code> 
  9.  <code>git add .</code> 
  10.  <code>git commit -m "initial commit"</code> 
  11.  <code>git push heroku master</code> 
  12.  <code>heroku db:push</code> 


Ta Da!

Plus I changed this line in environment.rb:
{% highlight ruby %}
config.middleware.use ::Radiant::Cache
{% endhighlight %}
  
to this:
{% highlight ruby %}
config.middleware.use ::Radiant::Cache,
:entitystore => "radiant:tmp/cache/entity",
:metastore => "radiant:tmp/cache/meta"
{% endhighlight%}
  
and I added a .gems file to the root directory:

{% highlight ruby %}
rspec --version 1.2.8
radiant --version 0.8.1
{% endhighlight%}
