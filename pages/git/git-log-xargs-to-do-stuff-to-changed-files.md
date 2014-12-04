---
layout: article
category: tools
title: Do stuff for changed files
level: 2
author: Aki
---

##### I needed to do upload changed files to server

I made some changes!

{% highlight bash %}
# git.rinkkasatiainen.fi$ git log --name-only --oneline -n1
# c369556 Adding new pages
# _includes/index-toc.html
# _layouts/git.html
# pages/git.md
{% endhighlight  %}

Now I needed to copy the files to a _tmp_ file

{% highlight bash %}
# git.rinkkasatiainen.fi$ cat tmp 
# _includes/index-toc.html
# _layouts/git.html
# pages/git.md
# pages/git/remove-files-from-git.html
{% endhighlight %}

And then the magic - run a command for every changed file:

{% highlight bash %}
# git.rinkkasatiainen.fi$  < tmp xargs -I % sh -c 'echo scp % \<server\>:.'
# scp _includes/index-toc.html <server>:.
# scp _layouts/git.html <server>:.
# scp pages/git.md <server>:.
# scp pages/git/remove-files-from-git.html <server>:.
{% endhighlight %}
