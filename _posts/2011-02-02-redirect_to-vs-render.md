---
layout: post
title: redirect_to vs. render - Rails
---
{{ page.title }}
================

redirect_to:
------------

* redirect_to causes the browser to receive a 302.
* The browser makes a brand new request and you will need to supply the browser with the information it needs to make the request such as the object attributes.
* Any existing variables will be lost.
* redirect_to is the right choice when you are posting a completely filled out form with valid data.

<br />
render:
-------

* render causes the browser to return a 200.
* The browser does not make a new request and instead just renders the page you specify without sending any information to it.
* The code in the rendered action will not be executed, it simply returns the view
* render is the right choice when a form was incorrectly filled out and you want to display errors on the page you were just on as well as saving state of all the data that had already been entered into the form. 

<br />
A link that helped me:<br />
[http://www.helloworlder.com/?p=6](http://www.helloworlder.com/?p=6)