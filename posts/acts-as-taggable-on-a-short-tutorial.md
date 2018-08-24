---
title: Acts as taggable on – A short tutorial?
date: '2012-08-22'
tags:
  - ruby-on-rails
layout: layouts/post.njk
---
Today I’m going to write a short and concise tutorial about how to use the awesome [acts\_as\_taggable\_on gem](https://github.com/mbleigh/acts-as-taggable-on/ "Acts as taggable on gem") in our Ruby on Rails application. You can read more about it on its github page I just linked, but I feel the documentation is not newbie friendly, and me being a n00b superhero, I decided to write down my own tutorial, both for the internet people, and for my own reference.

So, suppose you have your blog, kinda like this one you’re reading now. In this case, you would have a controller called posts. We are going to add tags to it. Let’s see how in 7 easy steps.

Open your Gemfile, add the following

```js
gem 'acts-as-taggable-on', '~> 2.3.1'
```

Open your terminal, navigate to your application, and run:

```js
bundle install
```

followed by

```js
rails generate acts_as_taggable_on:migration
```

and finally

rake db:migrate

Detect a model you want to add tags to (in my case, post.rb), and add a line just like this:

```js
acts_as_taggable_on :tags
```

Then in posts_helper.rb add

```js
include ActsAsTaggableOn::TagsHelper
```

We then need to add a way to add tags in our posts, so let’s edit the **posts/\_form.html.erb** file, and at the end of our form (and before the submit button) let’s add:

```js
<%= f.label :tags %>
<%= f.text_field :tag_list %>
```

Now we have to edit our view. In your posts/show.html.erb file, where you want to show the tags, add:

```js
<% @post.tags.any? %>
  <% @post.tags.each do |tag| %>
  <%= link_to tag.name, tagged_url(:tag => tag.name) %>
<% end %>
```

Meaning that unless there are no tags, the tags should be shown. Please note that “tagged” is the name of an action within our posts controller, and we are going to add it in our next step.

We now need to modify your posts controller.  
In the posts controller you need to add a new action which we can call tagged. This is the action we are going to show when a user clicks on a tag in our posts, so if you prefer you can call it whatever you like, but if you do, remember to change it in the steps above too.

```js
def tagged
  if params[:tag].present? 
    @posts = Post.tagged_with(params[:tag])
  else 
    @posts = Post.postall
  end  
end
```

This little code above would grab the tag value we are passing to the controller (if present), and would put it into the instance variable @posts.  
More in detail, this line:

```js
@posts = Post.tagged_with(params[:tag])
```

means:  
@posts will contain posts tagged with the tag parameter, quite self explainatory I believe.

Then, create a view for our Tagged action, which can be exactly the same as your index view (mine is, except for the title), and add a route to reach it in your routes.rb file, like so:

match 'tagged' => 'posts#tagged', :as => 'tagged'

**Please note that tagged_with is a functionality provided by the gem acts_as_taggable_on.**

So I hope this can help out all beginner rails programmers out there, please leave comments in case you spot errors or if you just want to add your two cents.

Credits: [g\-p.si](http://http//g-p.si/posts/tagging-with-acts-as-taggable-on) for the original tutorial, [abdul](http://abdul-barek-rails.blogspot.com/) for some code optimization, [maurizio](https://plus.google.com/100973969013103507046/about) for pointing out @posts is an instance variable.
