---
layout: article
category: tools
title: Add file to staging area
level: 2
author: Aki
---

##### Adding a file to staging area

I just created a new file: 

{% highlight bash %}
$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   pages/git.md
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	pages/git/add-file-to-staging.md
no changes added to commit (use "git add" and/or "git commit -a")
{% endhighlight %}

What should I do?


nowadays, I like patching more  - link to patching later

{% highlight bash %}
$ git add .
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#	modified:   pages/git.md
#	new file:   pages/git/add-file-to-staging.md
#
{% endhighlight %}

And then you can commit.

But, if your files are already tracked, you can do one command to use both 'git add .' and 'git commit -m &lt;message&gt;'

{% highlight bash %}
$ git commit -am "Adding file to staging"
[master 80700c1] Adding file to staging
{% endhighlight %}
