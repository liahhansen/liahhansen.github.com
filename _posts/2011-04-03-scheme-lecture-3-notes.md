---
layout: post
title: Scheme - Generalizing Functions
---
{{ page.title }}
================

These are notes I took while watching the third lecture of [Brian Harvey's 61A CS Class](http://webcast.berkeley.edu/course_details_new.php?seriesid=2010-B-26275&semesterid=2010-B)

Topic: Generalizing Functions

The code below can also be found [on the Berkeley website](http://inst.eecs.berkeley.edu/~cs61a/sp11/lectures/1.3/).

First we saw how to generalize our sumsquare function so that it can also work for sumcube:

{% highlight scheme %}
(define (sumsquare a b)
  (if (> a b)
      0
      (+ (* a a) (sumsquare (+ a 1) b)) ))

(define (sumcube a b)
  (if (> a b)
      0
      (+ (* a a a) (sumcube (+ a 1) b)) ))

(define (sum fn a b)
  (if (> a b)
      0
      (+ (fn a) (sum fn (+ a 1) b))))

(define (square x)
  (* x x))

(define (cube x)
  (* x x x))
{% endhighlight %}

Next we generalized functions that perform specific tasks such as returning a list of the even numbers from a list of both even and odd numbers:
{% highlight scheme %}
(define (evens nums)
  (cond ((empty? nums) '())
        ((= (remainder (first nums) 2) 0)
         (se (first nums) (evens (bf nums))) )
        (else (evens (bf nums))) ))
{% endhighlight %}

This function returns a list of words that have an 'e':

{% highlight scheme %}
(define (ewords sent)
  (cond ((empty? sent) '())
        ((member? 'e (first sent))
         (se (first sent) (ewords (bf sent))) )
        (else (ewords (bf sent))) ))
{% endhighlight %}

This function returns the pronouns of a sentence:

{% highlight scheme %}
(define (pronouns sent)
  (cond ((empty? sent) '())
        ((member? (first sent) '(I me you he she it him her we us they them))
         (se (first sent) (pronouns (bf sent))) )
        (else (pronouns (bf sent))) ))
{% endhighlight %}

This function generalizes the above functions so that we can use just one function to perform the same behavior as the above three functions:

{% highlight scheme %}
(define (filter pred sent)
  (cond((empty? sent) '())
       ((pred (first sent))(se (first sent)(filter pred (bf sent))))
       (else (filter pred (bf sent)))))
{% endhighlight %}

The most important word in computer science is *Abstraction*.  The second and third most important words are *Domain* and *Range*.

Domain: What kind of arguments does it take	

 * Example: domain of *=* is numbers whereas domain of *equal?* is anything

Range: Set of possible values a function can return

 * Example: predicate is a function whose range is true or false
	
Higher Order Function: A function that has a function as an argument and/or a function as a return value

First Class Data Type:

 * can be the value of a variable
 * can be an argument to a procedure
 * can be a value returned by a procedure
 * can be an element of a data aggregate

Data aggregate is like an array or a list, etc.

The way we define functions...like this:

{% highlight scheme %}
(define square (x) (* x x))
{% endhighlight %}

is actually shorthand for this:

{% highlight scheme %}
(define square(lambda (x) (* x x)))
{% endhighlight %}

The lambda is added in by the Scheme interpreter