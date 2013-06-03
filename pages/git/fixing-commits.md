---
layout: article
category: tools
title: Fixing Commits
level: 2
author: Aki
---

#### I accidentally
...added a commit to staging area? What to do?
{% highlight bash %}
$ git log --oneline
dc7aad8 Some Fancy commit message
1ca95df Some Fancy commit message
{% endhighlight%}

git reset to rescue!

{% highlight bash %}
$ git reset --hard HEAD^
HEAD is now at 1ca95df Some Fancy commit message
$ git log -1 --oneline
1ca95df Some Fancy commit message
{% endhighlight%}


#### committed wrong files to temp

I had done this
{% highlight bash %}
git add -- <file> <anotherfile>
...
git commit -am "message"
{% endhighlight %}

So, unintended -a options.

Fix with git reset --soft
{% highlight bash %}
git reset --soft HEAD^
git reset HEAD -- <file-that-should-not-be-commited>
git commit -c ORIG_HEAD
{% endhighlight %}