---
title: Rails console for beginners
date: '2012-07-12'
tags:
  - ruby-on-rails
layout: layouts/post.njk
---
Here I’d like to group some Rails console commands that are absolutely essential for every beginner.

To start the rails console, move to your project’s folder using the command line, and type:

```
rails c
```

The idea is to assign the content of a record to a variable, in this case here I’ve called it “u”, but you could call it whatever you like.

To find a user by login (where login is a field name, it could be anything else)

```
u  = User.find\_by\_login('username')
```

Find user by id (in this case, user 33)

```
u  = User.find(33)
```

Find all users with a certain parameter

```
u = User.where(:someparameter => 1830)
```

Get the last user

```
u = User.last
```

Get all users

```
u = User.all
```

Assign a value, in this case the (database) field name is ‘flag’

```
u.flag = true
```

or

```
u.name = 'Alex'
```

Save the value to database

```
u.save!
```
