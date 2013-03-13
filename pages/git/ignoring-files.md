---
layout: article
category: tools
title: Ignoring files
level: 2
author: Aki
---

#### ignoring files
Given a situation:

{% highlight bash %}
$ touch thisShouldNotBeInGit.txt
$ git status
# On branch master
# Your branch is ahead of 'origin/master' by 2 commits.
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	thisShouldNotBeInGit.txt
nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

This is easy way to fix it:
{% highlight bash %}
$ echo thisShouldNotBeInGit.txt >> .gitignore
$ cat .gitignore  # -->read the contents of .gitignore
.gitignore
_site
thisShouldNotBeInGit.txt
{% endhighlight %}
