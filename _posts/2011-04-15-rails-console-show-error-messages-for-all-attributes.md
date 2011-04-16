---
layout: post
title: Rails Console - Show Error Messages for All Object Attributes
---
{{ page.title }}
================

To view all of the errors on each of the attributes of your ActiveRecord
object (Rails 3), use Object.errors.full_messages:

{% highlight ruby %}

 > u = User.new
 => #<User id: nil, email: "", encrypted_password: "", reset_password_token: nil, remember_created_at: nil, sign_in_count: 0, current_sign_in_at: nil, last_sign_in_at: nil, current_sign_in_ip: nil, last_sign_in_ip: nil, confirmation_token: nil, confirmed_at: nil, confirmation_sent_at: nil, created_at: nil, updated_at: nil> 
 > u.save
 => false 
 > u.errors.full_messages
 => ["Email can't be blank", "Password can't be blank"]
{% endhighlight %}
