---
layout: article
category: tools
title: Feature branch - how to fetch those
level: 2
author: Aki
links:
  1: 
    Using feature branches: http://www.mariopareja.com/blog/archive/2010/01/11/how-to-push-a-new-local-branch-to-a-remote.aspx
---


##### Someone created a feature branch I need to fetch. 

This is how to do that[1](#link_1) (have not tried yet):

{% highlight bash %}
git fetch origin
git checkout -b quick-fix --track origin/some_name_i_dont_want_to_use
{% endhighlight %}
