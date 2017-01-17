---
title: Creating, hosting and deploying static sites
date: 2015-12-24 11:22:00
description: Best options available
---

The other day I came across this tweet.

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">Want simple static demo but github pages do not have https? Use heroku - it is almost as simple, see last section <a href="https://t.co/1lGR2j9hEh">https://t.co/1lGR2j9hEh</a></p>&mdash; Gleb Bahmutov (@bahmutov) <a href="https://twitter.com/bahmutov/status/679505001862017024">December 23, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Luck wants that I was also just looking into static sites. After purchasing a domain name I wanted to create a simple blog.

I replied to the tweet, explaining that Github Pages is still an option if you want SSL. You can for example use a service like [Cloudflare](https://www.cloudflare.com/). But more on that later.

Anyway, that tweet inspired me to write a blog post about the different ways you can create, host and deploy static sites. So here we go!

## 1. Github Pages
This is an awesome (free!) feature Github provides. You basically create a repo and start coding.
Once you're happy with the result just push your changes and you can immediately visit your creation on `<account-name>.github.io`
It's as easy as that!

You can also create [Project sites](https://pages.github.com/) instead of a User or Organization site. You can create unlimited Project sites. Isn't that convenient?

If you're looking for something more than just plain text, Github Pages has you covered. Because Github Pages are powered by [Jekyll](http://jekyllrb.com/), you can use Jekyll to organize your site and, say, make a blog.

It even supports custom domains. Just add a `CNAME` file to the root of your project and point your DNS records to GitHub IPs and you're all set!

For all info visit [Github Pages docs](https://pages.github.com/)

## 2. Heroku
> Heroku is a platform as a service (PaaS) that enables developers to build and run applications entirely in the cloud.

It's super easy to set up and they have great [documentation](https://devcenter.heroku.com/) for all sorts of languages.    

They also have a free tier, which is handy for little side projects.
However, the node sleeps after 30 mins of inactivity and needs to sleep for 6 hours in a 24 hour period.

Other cool things are that you can use a custom domain and that they provide SSL.

## 3. Divshot aka Firebase
I don't have any experience with this option but I keep hearing great thing about it. Divshot got acquired by Firebase which is a Google company. [Firebase](https://www.firebase.com/) also has a free tier, but doesn't allow custom domains. It does come with a free SSL certificate though.

More on [Firebase hosting here](https://www.firebase.com/hosting.html).

## Conclusion

I realize they are far more options to manage static sites out there, but I feel these are the more affordable, approachable of the bunch.

As you might have noticed I lean towards Github Pages. It basically offers everything you need. With one exception...

Like I mentioned in the beginning of the post, Github Pages do not provide SSL (yet).
You can however create a (free) Cloudflare account which can provide you with something they call "Flexible SSL".

<img class="x2 center" src="{{ site.baseurl }}assets/images/ssl.png" />

Note that this is not a full SSL solution. It only covers the part from the user to Cloudflare. But the connection from Cloudflare to your server is still served over http.

That's it! Hopefully this post will help and/or inspire you to get started on static sites!
