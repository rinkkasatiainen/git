---
layout: article
category: tools
title: Feature Branch
level: 2
author: Aki
links:
  1:
    Using feature branches : http://www.mariopareja.com/blog/archive/2010/01/11/how-to-push-a-new-local-branch-to-a-remote.aspx
---

##### I've heard that feature branches are good things? How's that

To be honest - no idea. Have never tried.

This is the way to create a new branch (from master)

{% highlight bash %}
$ git checkout -b feature-branch
Switched to a new branch 'feature-branch'
AMBWKS196:rinkkasatiainen.github.com akis$ git branch
* feature-branch
  master
{% endhighlight %}

Seeing your branches -> You can use gitk or SmartGit, or other tools.

Then doing some stuff on your branch. Commiting often.
You can push a new branch also to master [1](#link_1)

{% highlight bash %}
$ git push -u origin feature-branch
Username for ...
Password for ...
Counting objects: 28, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (24/24), done.
Writing objects: 100% (24/24), 4.08 KiB, done.
Total 24 (delta 17), reused 0 (delta 0)
To https://github.com/rinkkasatiainen/rinkkasatiainen.github.com.git
 * [new branch]      feature-branch -> feature-branch
Branch feature-branch set up to track remote branch feature-branch from origin.
{% endhighlight %}