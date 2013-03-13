---
layout: article
category: tools
title: See what's changed in your project
level: 2
author: Aki
---

##### how to cherry-pick


either by --no-commit

{% highlight bash %}
$ git cherry-pick --no-commit fetch-feature-branch ; git status
# On branch master
# Your branch is ahead of 'origin/master' by N commits.
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#	modified:   pages/git.md
#
{% endhighlight %}

or by commiting automatically

{% highlight bash %}
$ git status; git cherry-pick fetch-feature-branch; git status
# On branch master
# Your branch is ahead of 'origin/master' by N commits.
#
nothing to commit, working directory clean
[master d3e7282] A Cherry-pickable commit
 1 file changed, 2 insertions(+)
# On branch master
# Your branch is ahead of 'origin/master' by N+1 commits.
#
nothing to commit, working directory clean
{% endhighlight %}

