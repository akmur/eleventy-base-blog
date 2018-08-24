---
title: Enable pretty permalinks on localhost
date: '2013-02-11'
tags:
  - wordpress
  - apache
layout: layouts/post.njk
---
Just a quick and simple tip. If you are on ubuntu and working with WordPress on a local installation, and you are finding yourself in the situation of being unable to access your posts when you enable pretty permalinks (which is, a custom post structure in Settings > Permalinks), the reason could be that you simply need to enable mod rewrite on you local Apache server.

How to do it? Just open up your terminal and write:

```js
sudo a2enmod rewrite
```

followed by

```js
sudo service apache2 restart
```

Now everything should work!
