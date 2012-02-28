---
layout: post
title: "How to proper test named scopes"
date: 2012-02-28 20:18
comments: true
categories: [Ruby, Rails, TDD/BDD]
---

I just read few posts about *"how to test named scopes"*. It was tons of bullshit.
I am asking - why should I use FactoryGirl or raw models and create a lot of unnecessary stuff (objects, db rows etc.) just to test `order(:position).first`?!

But first, let's create `Post` model. Just an example for this note.

{% gist 1934188 %}

As you see, there are 2 simple scopes. I am not huge fan of Rails's named scopes - I use plain old class methods instead.

## How not to do this

{% gist 1919347 %}

We've just created .. let's count .. 5 objects and made 2 unnecessary db queries.

## How to do this

{% gist 1919368 %}

I think it's useless to test Rails's elements (like `where` or `order`). Rails is really proper tested.
Instead we should spec **messages** between object and passed **parameters**.