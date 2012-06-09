---
layout: post
title: "Rails: attr_accessor for HStore"
date: 2012-06-09 16:27
comments: true
categories: [Ruby, Rails, Hstore, PostgreSQL]
---

HStore is great feature in PostgreSQL. It allows us to use "mini-noSQL" db in out pg table. Nice!

Rails4 will have this baked-in, but now we have to use great gem [activerecord-postgres-hstore](https://github.com/softa/activerecord-postgres-hstore).

The only problem is, that there's no accessor methods. Let's assume that our model (Product) need price and weight. We will have to write something like this:

{% gist 2901202 %}

A lot of repetition. Definetly not DRY. We could use some metaprogramming and create this:

{% gist 2901210 %}

Nice, a lot cleaner. But maybe extract this so we could use it anywhere?

{% gist 2901165 %}

Now we can do this:

{% gist 2901225 %}
