---
layout: post
title: Understanding How Ruby Blocks Work
---
{{ page.title }}
================

I've been preparing the curriculum for a class about Ruby blocks.  The word "block" just means a block of code that gets passed to a method right after other parameters.  When a block is sent to a method, the code within it is then available to the method.  The method can call the block of code any time it wants to using the "yield" keyword.  To sum it up, the two important pieces of blocks, are:


# the code block
# the yield keyword



Look below...first I write my method, dos_veces.  When I call dos_veces, I add some code to the end of it between curly braces {...}.  That code gets executed by the method whenever I typed "yield" within my method definition. 

<img src='http://lh3.ggpht.com/_oEW94elB_a8/S1OmehH1OSI/AAAAAAAAADw/wJjWf5g20EU/blocks_dos_veces.png' width='400px'/>
<img src='http://lh3.ggpht.com/_oEW94elB_a8/S1OoUyBUgvI/AAAAAAAAAD4/dQqqls41HJY/super_powers_blocks.png' width='400px'/>


I've found a few extremely helpful websites including: <a href='http://eli.thegreenplace.net/2006/04/18/understanding-ruby-blocks-procs-and-methods/'>Eli Bendersky's blog post about blocks procs and methods</a>, <a href='http://www.robertsosinski.com/2008/12/21/understanding-ruby-blocks-procs-and-lambdas/'>Robert Sosinski's blog post about blocks, procs and lamdas</a>, <a href='http://rubylearning.com/satishtalim/ruby_blocks.html'>Ruby Learning: Blocks Tutorial</a>, and <a href='http://weblog.jamisbuck.org/2007/1/19/blocks-rock'>Jamis Buck's blocks rock post</a>.
