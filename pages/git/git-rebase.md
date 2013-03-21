---
layout: article
category: tools
title: Git Rebase, my best friend
level: 2
author: Aki
links:
  1:
     Mind your git manners : http://blog.8thlight.com/kevin-liddle/2012/09/27/mind-your-git-manners.html
---

##### git rebase is our best friend [1](#link_1)

Firstly, I do <code>git pull --rebase</code> so that my code looks like it's all written on top of the branch

{% highlight bash %}

       o-my-branch-o
      /
 o---o---master------o

{% endhighlight %}

and rebasing would make it look like:

{% highlight bash %}
                 o-my-branch-o
                /
 o---o--master-o
{% endhighlight %}

There's a reason for doing this, and it's about squashing multiple commits into one clump.

Say there would be a lot of those commits, like
{% highlight bash %}
                 o-my-branch-o---o---o---o---o
                /
 o---o--master-o
{% endhighlight %}

and in real:

{% highlight bash %}
$ git status; git log --oneline
# On branch master
# Your branch is ahead of 'origin/master' by 4 commits.
#
nothing to commit, working directory clean
0d472d9 Adding some commit which does not make sense to document
83b4fc7 syntax highlight for 'git pull --rebase'
62a0573 Adding page for git-rebase
80700c1 Adding file to staging
184ec91 Adding notes from AulankoOpenSpace 2013 notes from AulankoOpenSpace
{% endhighlight %}

which we'd like to squash into one commit: Along comes git rebase

{% highlight bash %}
$ git rebase -i 184ec91 # commit-sha of the last commit that we don't want to squash
#normally would be that of 80700c1, but now showing one piece of details	
{% endhighlight %}

Calling that you get a scary-looking text opened in VI

{% highlight raw %}
pick 80700c1 Adding file to staging
pick 62a0573 Adding page for git-rebase
pick 83b4fc7 syntax highlight for 'git pull --rebase'
pick 48b95ad Adding some commit which does not make sense to document

# Rebase 184ec91..48b95ad onto 184ec91
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
{% endhighlight %}

and after editing comes like this

{% highlight text %}
pick 80700c1 Adding file to staging
p 62a0573 Adding page for git-rebase
s 83b4fc7 syntax highlight for 'git pull --rebase'
f 48b95ad Adding some commit which does not make sense to document
[...]
{% endhighlight %}

after which some more documentation and ...

{% highlight bash %}
$ git rebase -i 184ec91
[detached HEAD c14565a] git-rebase Adding page for git-rebase
 3 files changed, 111 insertions(+), 5 deletions(-)
 create mode 100644 pages/git/git-rebase.md
Successfully rebased and updated refs/heads/master.
$
{% endhighlight %}


And this is what the log will look like:

{% highlight bash %}
$ git status; git log --oneline
# On branch master
# Your branch is ahead of 'origin/master' by 2 commits.
#
nothing to commit, working directory clean
430b6ba git-rebase Adding page for git-rebase
80700c1 Adding file to staging
184ec91 Adding notes from AulankoOpenSpace 2013 notes from AulankoOpenSpace
{% endhighlight %}
