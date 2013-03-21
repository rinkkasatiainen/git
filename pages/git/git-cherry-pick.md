---
layout: article
category: tools
title: Cherry-picking commits
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


#### CASE!

Q: I've been working on a master for quite some time and commiting often to (local) master branch. Now I noticed that I need to push one change to repository master. How do I do that?

A: You need to cherry-pick that particular commit to a origin/master HEAD. And for that, you need a branch that has only the latests in origin/master HEAD.
 1. create a new branch from origin/master
 1. cherry-pick the one commit you need to push to repository
 1. push commit
 1. delete branch


