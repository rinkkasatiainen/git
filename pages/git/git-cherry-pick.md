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

So, the workflow: gi

{% highlight bash %}
git status ; git log --oneline -5
# On branch gh-pages
# Your branch is ahead of 'origin/gh-pages' by 4 commits.
#
nothing to commit, working directory clean
df7f75e It compiles, but tests do not pass!
7a8c6c6 Still working on stuff, does not compile
b9151ca This is commit I want to push to master! #<-- this I want to push to master""
db0f602 Adding a CASE for cherry-picking
99cd3fa CNAME
{% endhighlight %}

Create new branch from origin/master
{% highlight bash %}
$ git fetch; git checkout -b fastfix origin/gh-pages
Branch fastfix set up to track remote branch gh-pages from origin.
Switched to a new branch 'fastfix'
{% endhighlight %}

Then cherry-pick

{% highlight bash %}
$ git cherry-pick --no-commit b9151ca
AMBWKS196:git.rinkkasatiainen.fi akis$ git status
# On branch fastfix
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
< new and modified files, changes from the cherry-picked commit >
#

{% endhighlight %}


And push

{% highlight bash %}
$git commit -m "cherry-pick b9151ca"
[fastfix e52c19b] cherry-pick b9151ca
 5 files changed, 17 insertions(+), 9 deletions(-)
 create mode 100644 _includes/references.html
$ git push origin fastfix:gh-pages
Username for [...]
Password for [...]
Counting objects: 19, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (11/11), done.
Writing objects: 100% (11/11), 1.30 KiB, done.
Total 11 (delta 6), reused 0 (delta 0)
To https://github.com/rinkkasatiainen/git.git
   99cd3fa..e52c19b  fastfix -> gh-pages
$ 
{% endhighlight %}