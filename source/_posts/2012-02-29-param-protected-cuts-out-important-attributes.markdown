---
layout: post
title: "param_protected cuts out important attributes"
date: 2012-02-29 14:22
comments: true
categories: [Ruby, Rails, Gem]
---

I am huge fan of [param_protected](https://github.com/cjbottaro/param_protected)
which I use instead of [attr_accessible](http://api.rubyonrails.org/classes/ActiveModel/MassAssignmentSecurity/ClassMethods.html#method-i-attr_accessible)/[attr_protected](http://api.rubyonrails.org/classes/ActiveModel/MassAssignmentSecurity/ClassMethods.html#method-i-attr_protected).

I think it's not model thing to allow or deny attributes. Ok, maybe in case of User model I would protect it in controller and model too.

Anyway, it turns out that param_protected cuts out some really important parameters - like `action` or `commit`.

It is super easy to fix, but unfortunately it's not mentioned in documentation. So, let's add out parameters whitelist.

{% gist 1940847 %}

`controller`, `action` and `id` are self-explanatory. `utf8` and `commit` are used by Rails forms

I added some additional attributes:

* `authenticity_token` which is used by Devise (maybe some other auth gems too)
* `page` which is used by will_paginate/kaminari

`page` is allowed only on `index` action, because that's where pagination is used

***

This post is rewrite of *"[param_protected wycina potrzebne parametry](http://kzalewski.blogspot.com/2012/01/paramprotected-wycina-potrzebne.html)"*
from my previous blog.
