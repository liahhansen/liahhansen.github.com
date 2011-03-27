---
layout: post
title: Escaping and Unescaping in HAML
---
{{ page.title }}
================

To turn escaped HTML into HAML, use <code>!=</code> instead of just <code>=</code>
To escape unescaped HTML, use <code>&=</code> instead of just <code>=</code>.

{% highlight bash %}
> Haml::Engine.new('!= "<p> Hello World</p>"').render<br>
=> "<p> Hello World</p>\n" <br>
> Haml::Engine.new('%p Hello World').render<br>
=> "<p>Hello World</p>\n" <br>
> Haml::Engine.new('= "<p> Hello World</p>"').render<br>
=> "<p> Hello World</p>\n" <br>
{% endhighlight %}

Resources:

<a href="http://haml-lang.com/docs/yardoc/file.HAML_REFERENCE.html#unescaping_html">Unescaping HTML</a><br />
<a href="http://haml-lang.com/docs/yardoc/file.HAML_REFERENCE.html#escaping_html">Escaping HTML</a>
