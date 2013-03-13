---
layout: article
category: tools
title: Pushing changes to repository
level: 2
author: Aki
---

#### push to master
given a situtation

{% highlight bash %}
$ git status
# On branch master
# Your branch is ahead of 'origin/master' by 3 commits.
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   pages/git.md
#
no changes added to commit (use "git add" and/or "git commit -a")
{% endhighlight%}

There are already 3 commits I haven't pushed upstream. Now I need to stage those local commits:
{% highlight bash %}
$ git commit -am "Help for 'push to master'"
[master a66e9e7] Help for 'push to master'
 1 file changed, 22 insertions(+), 2 deletions(-)
$ git status
# On branch master
# Your branch is ahead of 'origin/master' by 4 commits.
#
nothing to commit, working directory clean
{% endhighlight %}

And then to push those 4 new commits to master
{% highlight bash %}
$ git push origin master
Username for 'https://github.com': rinkkasatiainen
Password for 'https://rinkkasatiainen@github.com': 
Counting objects: 30, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (24/24), done.
Writing objects: 100% (24/24), 3.54 KiB, done.
Total 24 (delta 14), reused 0 (delta 0)
To https://github.com/rinkkasatiainen/rinkkasatiainen.github.com.git
   dc11978..d473f9f  master -> master
{% endhighlight %}
