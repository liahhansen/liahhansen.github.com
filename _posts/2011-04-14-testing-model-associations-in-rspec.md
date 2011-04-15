---
layout: post
title: Testing Model Associations in Rspec (Rails 3)
---
{{ page.title }}
================

I live with five really awesome housemates.  Five warm bodies tend to
make a mess by the end of the week so we have a chore chart on the
fridge.  I tend to be the one who
badgers everyone else into doing their weekly chore - not my favorite
thing to do...so, I figure it's time to put Rails to work sending
those emails for me.  

I named our fridge chore chart replacement *Choretle*.  I'm excited to get it finished so that it can do all the dirty work of emailing
reminders and doling out appropriate praise for a job well done.

I've got my data model pretty much sorted out at this
point and I just started generating my models.  I decided to do some
googling about testing model associations since it has never been as streamlined as I'd like.  I found a
couple of ways to test associations, some of them better than others.

The way I've tested associations in the past has gone something like
this:

{% highlight ruby %}
describe Group do
  it "should respond to users" do
    g = Group.new
    g.should respond_to(:users)
  end
end
{% endhighlight %}

What I don't like about it is that it is a round-about way of testing
for an association.  It tests a side effect of the association, not that
the association exists.

The next solution I found is built  into ActiveRecord::Reflection::AssociationReflection, so no need to install extra gems:
  
{% highlight ruby %}
>  g = Group.reflect_on_association(:users)
 => #<ActiveRecord::Reflection::ThroughReflection:0x00000100d65208 @macro=:has_many, @name=:users, @options={:through=>:affiliations, :extend=>[]}, @active_record=Group(id: integer, name: string, creator: integer, created_at: datetime, updated_at: datetime), @collection=true> 
> g.macro
 => :has_many 
{% endhighlight %}

The <code>macro</code> method makes it fairly easy to write an
association test:

{% highlight ruby %}
describe Group do
  it "should have many users" do
    g = Group.reflect_on_association(:users)
    g.macro.should == :has_many
  end
end
{% endhighlight %}

It is still kinda ugly don't you think?  Definitely not an elegant way
to indicate the relationship.  Luckily, I found a couple of
recommendations for gems that make for more descriptive syntax: remarkable and shoulda.  Both gems have similar syntax:
{% highlight ruby %}
#both remarkable and shoulda use this syntax
    describe Group do
      it { should belong_to(:supergroup) }
      it { should have_many(:users) }
    end
{% endhighlight %}


Remarkable seems cool, but from what I could tell, it isn't well maintained.  The last commit is from about a year ago on the [carlosbrando fork](https://github.com/carlosbrando/remarkable).  

I decided to use Shoulda for my tests.  It's easy to get working - just
add <code>gem 'shoulda-matchers'</code> to the Gemfile.  

Here is my (short and symantically relevent) model association test:

{% highlight ruby %}
  describe Group do
    it { should have_many(:users)}
  end
{% endhighlight %}

In my research, I encountered some debate about whether testing
associations is
worthwhile in the first place.  Some people argue that it is testing Rails instead of your own code.  I'd argue that testing
associations isn't testing Rails.  It is testing that your code is
hooked up the way you want it.  Testing associations also gets me into
the
TDD frame of mind as soon as I start a project.  Plus, when Shoulda makes it so easy,
I don't have any excuses not to test associations.
