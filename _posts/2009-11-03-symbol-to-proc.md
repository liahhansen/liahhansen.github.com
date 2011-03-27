---
layout: post
title: Symbol to Proc
---
{{ page.title }}
================

I was tri-programing with S & B today, writing Selenium tests.  S typed: 

{% highlight ruby %}
People.all.map(&:name)
{% endhighlight %}

into irb to demonstrate a database call.  I've seen this syntax before, but never understood what it meant. He said he didn't know, but that it worked. The output is an array of the names of all the People: 

{% highlight ruby %}
["Sandra", "Bob", "Fred", "Rosey"]
{% endhighlight %}

B explained that the ampersand followed by a symbol is a concise syntax for mapping the symbol object to a block.

Here is a bit of playing with irb that illustrates how Symbol#to_proc works:

{% highlight ruby %}
>> People.all
=> [#<People id: 2, name: "Sandra">, #<People id: 3, name: "Bob">, #<People id: 4,  name: "Fred">, #<People id: 5,  name: "Rosey">]

>> People.all.map(&:name)
=> ["Sandra", "Bob", "Fred", "Rosey"]

>> People.all.collect { | t | t.name }
=> ["Sandra", "Bob", "Fred", "Rosey"]

>> :name.to_proc
=> #<Proc:0x00002b720b0f45f8@/usr/local/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/core_ext/symbol.rb:11>

>> mything = proc { | t | t.name }
=> #<Proc:0x00002b720f91e950@/home/heroku_rack/lib/console.rb:133>

>> People.all.map(&mything)
=> ["Sandra", "Bob", "Fred", "Rosey"]

>> People.create!(:name => "Ben")
=> #<People id: 9, created_at: "2009-11-02 13:25:55", updated_at:
"2009-11-02 13:25:55", name: "Ben", creator_id: nil>

>> People.all.map(&mything)
=> ["Sandra", "Bob", "Fred", "Rosey", "Ben"]
{% endhighlight %}

In a nutshell, the following two lines of code have the same result:

{% highlight ruby %}
People.all.map(&:name)
People.all.map( | t | t.name)
{% endhighlight %}
