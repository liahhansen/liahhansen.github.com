---
layout: post
title: SICP 1 - Functional Programming, Applicative Order, Normal Order
---
{{ page.title }}
================

These are notes I took while watching the first lecture of [Brian Harvey's 61A CS Class](http://webcast.berkeley.edu/course_details_new.php?seriesid=2010-B-26275&semesterid=2010-B)

**Functional programming:**
Output will always be the same if the input is the same - this is helpful in ensuring consistency when we run the same program on different processors (parallel processing)

**Applicative order evaluation:**
All the arguments to Scheme procedures are evaluated when the procedure is applied
in other words, arguments are evaluated before procedures

**Normal order evaluation:**
Evaluation of procedure arguments is delayed until the actual argument values are needed. Delaying evaluation of procedure arguments until the last possible moment (e.g., until they are required by a primitive operation) is called lazy evaluation.

You are only assured of getting the right answer with both applicative and normal order evaluation when using functional programming.  The following example illustrates how if we don't follow the rules of functional programming (same output for same input), we may get different results for normal vs applicative evaluation.

{% highlight ruby %}
def zero(x)
	x - x
end
{% endhighlight %}

**Applicative**: will always give zero because the argument is evaluated before the procedure is applied:
{% highlight ruby %}
zero(10.rand)
{% endhighlight %}

**Normal**: will give varying answers because the entire 10.rand expression is substituted for each of the x’s in the procedure:

{% highlight ruby %}
zero(10.rand)
{% endhighlight %}

In this case by using rand we are breaking the rules of functional programming.   rand is not a function since a function by definition gives the same outputs for the same inputs.  Since it isn’t a function and we aren’t doing functional programming, the order in which things happen matters.

Moral of the story: if you are doing functional programming, order doesn’t matter.

**Efficiency can also be different for applicative vs. normal**

Efficiency difference using the square function:

{% highlight ruby %}
def square(x)
	x*2
end
{% endhighlight %}

applicative:

{% highlight ruby %}
square(2+3)
{% endhighlight %}

2+3 is evaluated once

normal:
{% highlight ruby %}
square(2+3)
{% endhighlight %}

2+3 is evaluated four times

There is a way to do things so that normal order comes out to be more efficient, but in this case  applicative was more efficient.  In any case, the point is that you need to think about the order in which operations are performed.