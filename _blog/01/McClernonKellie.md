---
title: "Blog 1: Getting started with git"
author: "Kellie McClernon"
topic: "01"
layout: post
root: ../../../
---

## Reflection Questions:

1. **Looking back at all of the team projects you have been involved in, describe the biggest mishap you had. Could that have been avoided using git? How?**. 

We had a team project to convert an automated workflow from the legacy system to a new processing system. One coworker was in another country and timezone during the project. Whenever I noticed an error in the duplication of the system, I would take a screenshot and send an email noting the change necessary. Not only was this a laborious process, but several times my emails would go unactioned (easily enough to be done since I was sending several a day) or the resulting change would be incorrect, necessitating another email. If we had a versioning system like git, I could have created an independent branch and made changes without impacting the master (or live) version. Then once all changes had been approved, my branch could be merged back to the master.

2. **Give an example of one new git feature that you learned about from Jenny Bryan's book.**.

I had tried to use git in the past for a group project but I was confused about what exactly forking and branching did. Therefore, I chose to read about branching specifically. Now I understand how branching enables collaborative, simultaneous editing of a workflow by creating an individual copy that can be edited and saved independent of the master. When the branch is completed and ready to be joined back to the master, git ensures that no conflicts with the master are committed. Forking however does not have such a direct connection with the master file. Instead changes are committed with a pull request.
