---
title: Associations in Ruby on Rails
date: '2012-09-19'
tags:
  - ruby-on-rails
layout: layouts/post.njk
---
Associations between models are used for easier coding, and they make it possible to “chain” methods between associated models.

An example will clarify this.  
Imagine we have a model for our blog posts, post.rb, and a model for our categories. We want the post to belong to a category and a a category to have many posts.  
To do this, we add

```js
belongs_to :category
```

to our post.rb file,

and we add

```js
has_many :posts 
```

to our category.rb file.

What this does is to tell our application what kind of relationship there is between the two models.  
To make the above work, we will need to add a column in our database. This column should go in the posts table, and it should be called category_id. This way we can save the id of the category the post belongs to. This will allow us to open up a world of cool stuff.

We will make it possible to do stuff like:

```js
@post.category.name
```

Here, this would output the name of the category my post belongs to.  
It’s like having chaining superpowers!

Neat, right? For plenty of information about this topic, head straight to the official [ruby guides](http://guides.rubyonrails.org/association_basics.html)
