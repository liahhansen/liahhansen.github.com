---
layout: post
title: First Program in C
---
{{ page.title }}
================

Now that I've got Ruby and Rails fairly well learned and practiced, I decided it was time to start working towards learning some lower level languages.  Here is my first baby step towards learning C:

{% highlight bash %}
touch foo.c
{% endhighlight %}
<br />
{% highlight bash %}
mate foo.c`
{% endhighlight %}

In foo.c I wrote (with the help of my roommate Sean):

{% highlight c %}
#include <stdio.h>
int main() {
	int i;
	printf("Hello World!!!!!!\n");
	for(i=0; i<5; i++) {
		printf("%d\n", i);
	}
	return 0;
}
{% endhighlight %}


Next, I compiled my program:

{% highlight bash %}
gcc foo.c
{% endhighlight %}


This created a file called a.out

Next I ran a.out

{% highlight bash %}
./a.out
{% endhighlight %}

And it out put:

{% highlight bash %}
Hello World!!!!!!
0
1
2
3
4
{% endhighlight %}

Sean also taught me how to define the name of the out file:

{% highlight bash %}
gcc -o foo foo.c
{% endhighlight %}

This let me do the following to execute my program:

{% highlight bash %}
./foo
{% endhighlight %}

