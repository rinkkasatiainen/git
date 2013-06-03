---
layout: article
category: tools
title: See what's changed in your project
level: 2
author: Aki
---

#### Wanna see logs?
so-called one-liner?

{% highlight bash %}
$ git log --oneline
{% endhighlight %}

A bit more information:

{% highlight bash %}
$ git log --format=[oneline|short|medium|full|fuller|email|raw]
{% endhighlight %}
 if omitted, 'medium' by default

Show the 5 most recent commits - 3 ways to do it:
{% highlight bash %}
$ git log HEAD~5..HEAD --oneline  #show last 5 commits as one line
$ git log HEAD^^^^..HEAD --oneline  #show last 5 commits as one line
$ git log -5 --oneline  #show last 5 commits as one line
{% endhighlight %}


#### What has changed?
What's changed in your working tree, compared to the staging area
{% highlight bash %}
$ git diff
{% endhighlight %}

Differences in between the staged changes and the repository

{% highlight bash %}
$ git diff --staged
{% endhighlight %}

Changes between working tree and the repository HEAD
{% highlight bash %}
$ git diff HEAD
{% endhighlight %}


#### What has changed <since>
