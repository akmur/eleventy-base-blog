---
title: Beginning Ruby - What is a class?
date: '2012-07-18'
tags:
  - ruby
layout: layouts/post.njk
---
Here I am again, with my beginner’s guide to Ruby (on Rails).  
Today I just want to briefly talk about classes.

**Classes are the “blue prints” used to create objects** in Ruby. They basically tell our computer that we are creating an object (example: a dog) with certain characteristics (example: breed, name, color).

In my [previous ruby post](/posts/beginning-ruby-what-is-a-method/ "Beginning Ruby: What is a method?"), i talked about methods, and methods are used in classes to define sets of instructions. So, let’s make a real\-world rails example. Here’s an example of how a controller looks like in a blog made with RoR. A controller is a class and in this case this is “controlling” the behaviour of our posts page.

```ruby
class PostsController < ApplicationController 
  def index
    @posts = Post.all
  end
  def new
    @post = Post.new
  end
end
```

We have a class, PostsController, containing a method called index and another one called new. Inside this methods we have a function or an instruction.

So, remember this: **classes are blueprints used to make objects. Classes use methods to define which instructions need to be run.**

When starting out with RoR, (for example by using scaffolding), classes and methods will be already written for us by the automatic generator, but as we progress we will find that it’s quite common to create our own methods and classes. More on this soon!
