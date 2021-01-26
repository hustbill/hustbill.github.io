---
title: Git Operations
date: 2016-06-26 09:30:00
categories: 
tags:
    - git
---

Git Operations
---------------

1. How to remove local untracked files from the current Git branch
To remove directories, run git clean -f -d or git clean -fd.  
To remove ignored files, run git clean -f -X or git clean -fX.  
To remove ignored and non-ignored files, run git clean -f -x or git clean -fx.  

2.  reset to an absolute commit SHA1 value  
```
 git reset 5d125c
```

3. Git submodule
```code
git submodule add https://github.com/fi3ework/hexo-theme-archer.git themes/archer
```

4. Change branch name
```code
git branch -m master main
git fetch origin
git branch -u origin/main main

```

5. [How do I delete a Git branch locally and remotely?](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-locally-and-remotely)
```code
$ git branch -d branch_name
$ git branch -D branch_name

git push -d <remote_name> <branch_name>
# Note that in most cases the remote name is origin. In such a case you'll have to use the command like so.
$ git push -d origin <branch_name>

```

6. Squash my last X commits together using Git  
Use ```git rebase -i <after-this-commit> ``` and replace "pick" on the second and subsequent commits with "squash" or "fixup", as described in [the manual](https://git-scm.com/docs/git-rebase#_interactive_mode).


7. [How to modify existing, unpushed commit messages?](https://stackoverflow.com/questions/179123/how-to-modify-existing-unpushed-commit-messages)
Amending the most recent commit message
```
git commit --amend -m "New commit message"
```

Changing the message of a commit that you've already pushed to your remote branch
If you've already pushed your commit up to your remote branch, then - after amending your commit locally (as described above) - you'll also need to force push the commit with:
```
git push <remote> <branch> --force
```

