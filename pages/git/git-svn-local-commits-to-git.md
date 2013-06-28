---
layout: article
category: tools
title: Special workflow, great success in moving stuff from SVN to GIT 
level: 2
author: Aki
---

##### I had this great success. 

We had stuff in SVN and then we moved those to git. While I had a bunch of local commits not pushed to SVN, I went for a holiday. And when coming back, all code was in git. What to do.

1. set remote to git repository
2. create new branch from feature branch [described here](/git/fetch-feature-branch.html)
3. cherry-pick commits from git-svn l_devel branch to the new git-based branch. I used --no-commit to verify things were OK.
  > possibly commit
4. push to master: git push git-repository git-based-branch:master
