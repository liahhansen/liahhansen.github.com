---
layout: post
title: Scheme - Sum of Biggest Squares, Lambda Calculus (Noisebridge Notes)
---
{{ page.title }}
================

I just got home from the [Noisebridge Schemers](https://www.noisebridge.net/wiki/Schemers) meetup.  We started off talking about problem 1.2 (1985 version) / 1.3 (1996 version).  Here's the problem:

> Define a procedure that takes three numbers as arguments and returns the sum of the squares of the two larger numbers

Here is our first implementation:

{% highlight scheme %}
(define ssq2(a, b, c)
  (and (a<=b) (a<=c))(sum_of_squares b c)
  (and (b<=a) (b<=c))(sum_of_squares a c)
  (and (c<=a) (c<=b))(sum_of_squares a b)
)
{% endhighlight %}

We talked about how writing this function in scheme involves thinking in a different way than if we were to write it in Ruby.  In Ruby we might sort the arguments using a sort method, then eliminate the smallest one.  Ruby gives us sort and min/max methods for free.  In Scheme it isn't quite so easy.  In Scheme we think about the problem more in terms of a tree whereas in Ruby we manipulate our data in memory using methods.  To illustrate this point, we considered the following code which is how we might think about the problem in a Rubyish way.  It assumes that there is a sort method that takes a greater than or less than symbol to determine whether to sort ascending or descending.  

{% highlight scheme %}
(define(ssq2 a b c)
  (+ (* (car(sort(list a b c) >)
        (car(sort(list a b c) >)))
      (* car(cdr(sort(list a b c) >)))
         (car(cdr(sort(list a b c) >)))))
{% endhighlight %}

Here is my implementation in Ruby using a Scheme-like design.

{% highlight ruby %}
def sum_square_two_biggest(a,b,c)
  if a<=b && a<=c
    sum_of_squares b c
  elsif b<=c && b<=a
    sum_of_squares c a
  else
    sum_of_squares a b
  end 
end
{% endhighlight %}

This is an asci art tree that demonstrates how a Schemer might think about the problem.  The left branches are the result of the node being true.

{% highlight ruby %}

                a<b
              /      \
            /           \
          |                |   
        b<c                  a<c     
      |     |              |       |
      |     a<c            |       c<b
      |     |    \         |     |      |      
   a<b<c   a<c<b   c<a<b  b<a<c   c<b<a   b<c<a   
{% endhighlight %}
 
We talked about functional programing and how using <code>set!</code> breaks functional programming. Don't use <code>set!</code> if you want to use applicative evaluation as it forces evaluation immediately.  On the other hand, using <code>define</code> expands into a lambda expression and does not break functional programming rules.

Lambda example:

{% highlight scheme %}
((lambda(n) (+ n 1)) 41)

=> 42
{% endhighlight %}

Lambda calculus example:

{% highlight ruby %}
(λx|x) a
=> a

(λx|x)(λy|yy)
=> (λy|yy)
(λy|yy)(λx|x)
=> (λx|x)(λx|x)
=> (λx|x)
{% endhighlight %}


Book recommendation for lambda calculus: algorithmics by david harel


