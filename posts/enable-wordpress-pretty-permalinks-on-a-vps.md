---
title: Enable WordPress Pretty Permalinks
date: '2013-04-29'
tags:
  - wordpress
  - devops
layout: layouts/post.njk
---
Scenario: You have a VPS, you have installed Apache, MySQL, PHP and WOrdpress, and you want to enable pretty permalinks.
If you’re getting a 404 error when accessing your WordPress posts after having enabled “pretty permalinks” in the settings, then this is how to solve the issue (at least it worked for me).

Log in into your VPS server.

```js
ssh username@IP-ADDRESS
```

then let’s get to the sites-enabled folder

```js
cd /etc/apache2/sites-enabled
```

Here there is a file called 000-default

using something like nano (a simple text editor) open this file:

```js
sudo nano 000-default
```

Now that the file is open, you’ll see something like this:

```js
DocumentRoot /var/www

Options FollowSymLinks
AllowOverride None

Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
Allow from all
```

What we need to do is to change those two “AllowOverride None” to “AllowOverride All”.

Once it’s done, just restart your apache server

```js
/etc/init.d/apache2 restart
```

And your pretty permalinks should be working now! Nice!
