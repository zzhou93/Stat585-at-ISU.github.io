---
title: "Happy git"
author: "Yudi Zhang"
topic: "01"
layout: post
root: ../../../
---

Write a blog post answering the following questions: 

1. **Looking back at all of the team projects you have been involved in, describe the biggest mishap you had. Could that have been avoided using git? How?**. 

Last summer, I started to involved in research using C programming, however I couldn't link the Rmath library and one guy suggested on StackOverflow to use "git clean" first and it can be installed successfully. However, I lost everything in my computer after I used that command. Apparently, it is caused by unfamiliarity with git.  Well, this disaster could be resolved by carefully reading the manual and perhaps see some examples before using git. 

2. **Give an example of one new git feature that you learned about from Jenny Bryan's book.**.

From chapter 26, I get to know multiple ways to solve conflicts when you try to `git pull`. We can do `git stash` -> `git pull` -> `git stash pop` -> solve the conflicts -> `git reset` -> `git stash drop`.
What’s more, I finally figured out the difference between “origin” and “master”.  By using `git remote`, usually you get origin: the shortname created by git to refer to your remote repo. Use `git branch`, the default branch is master, the place where you are currently working on. So, the origin is like a handle, point out where the branches are.
