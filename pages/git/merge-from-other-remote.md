---
layout: article
category: tools
title: Merge from other remote
level: 2
author: Aki
---

##### Merge from other remote:


1. Set remote origin 
{% highlight bash %}
git remote add www https://github.com/rinkkasatiainen/rinkkasatiainen.github.com.git
{% endhighlight %}

1. pull from remote
{% highlight bash %}
git fetch www branches
{% endhighlight %}

1. create local branch
{% highlight bash %}
git checkout -b www-using-branches --track www/using-branches
{% endhighlight %}

1. merge
{% highlight bash %}
git merge using-branches
{% endhighlight %}
