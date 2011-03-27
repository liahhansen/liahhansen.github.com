---
layout: post
title: Double Colon
---
{{ page.title }}
================

I'm reading Refactoring: Ruby Edition and I came across the double colon (::) operator.  I pretty much understand what it means, but I thought I'd do a little more research to get a better handle on its intricacies.  I came across the code below at http://en.wikibooks.org/wiki/Ruby_by_examples#:: 

{% highlight ruby %}
CONST = ' out there'

class Inside_one
    CONST = proc {' in there'}
    def where_is_my_CONST
       ::CONST + ' inside one'
    end
 end
 
 class Inside_two
    CONST = ' inside two'
    def where_is_my_CONST
       CONST
    end
 end
{% endhighlight %}

I thought I'd try it out in irb.  Here is the output:

{% highlight bash %}
>> puts Inside_one.new.where_is_my_CONST
 out there inside one

>> puts Inside_two.new.where_is_my_CONST
 inside two

>> puts Object::CONST + Inside_two::CONST
 out there inside two

>> puts Inside_two::CONST + CONST
 inside two out there

>> puts Inside_one::CONST
#<Proc:0x00000001012ac4a0@(irb):3>

>> puts Inside_one::CONST.call + Inside_two::CONST
 in there inside two
{% endhighlight %}
 
