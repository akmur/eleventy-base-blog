---
title: Beginning Ruby - What is a method?.
date: '2012-06-18'
url: beginning-ruby-what-is-a-method
tags:
  - ruby
layout: layouts/post.njk
---
I am a forever\-noob kind of person, and I’m currently studying [Learn Ruby the Hard Way](http://ruby.learncodethehardway.org/ "Learn ruby the hard way"), a very effective (and not hard at all) way to learn to program.

In one of the exercises, it asks you to list a lot of ruby keywords, and among those there are fundamentals like methods, classes, and so on. Now, since I have a 3 seconds memory, it is very hard for me to send all this info to memory, that is why I decided to put down my findings here.

Enough for the intro, so:

**What is a Ruby method?**

Methods in Ruby are what other languages refer to as “functions”. Ruby methods are used to bundle together a set of instructions that can be called back at any point in our program.

Example:

```ruby
def hello
    "hello"
end

puts hello
```

Methods should be created before calling them, otherwise you would get an error when running your program.  
We do not have to declare a return type, because the value of the last statement is automatically returned when the method is called.  
Some methods might need arguments, while some others don’t. When they don’t we don’t use parenthesis at all. If they do, they would look like:

```ruby
def hello(arg1, arg2)
  puts "this is #{arg1} and this is #{arg2}"
end

arg1 = gets.chomp
arg2 = gets.chomp

hello(arg1, arg2)
```

Simple enough!
