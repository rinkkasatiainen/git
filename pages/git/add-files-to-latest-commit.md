---
layout: article
category: tools
title: So, I did not run unit tests when committing to staging?
level: 2
author: Aki
---

#### It has happened, I've committed code that does not compile.

No worries.

    here you see me hacking around. Relentlessly...

and then:

{% highlight bash %}
$ git add .
$ git commit --amend -C HEAD
{% endhighlight %}
