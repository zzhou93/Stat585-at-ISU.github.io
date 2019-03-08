---
title: "All that legal stuff..."
author: "Eryn Blagg"
topic: "07"
layout: post
root: ../../../
---

## Background:

The `DESCRIPTION` file of a package contains the package's meta information. Most of the fields in this file are quite straight forward: author, version number, and a short package description. When you call `library(help="<package name>")` for  package `<package name>` you can see the contents of the `DESCRIPTION` file for that package (and some parts of the `NAMESPACE` file).

Read through the chapter on [metadata](http://r-pkgs.had.co.nz/description.html) from Wickham's book on R packages. 

Here, we want to focus on the use of licenses in R packages.
There are several important aspects to consider when choosing a license for your work. 
Three of the main questions to answer are: 

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?


Write a blog post addressing the following questions: 

1. **Under what license does R operate?**

  R operates under the GNU General Public License, version 3 (GPL-3).

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

  **MIT:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
   It lets people use and freely distribute your code subject but the license must always be distributed with the code.
      
  2. Are you and your collaborators fine with other people making a profit from those derivations?
  
    Anyone can make a profit with derivatives of the original work, as long as they include the license along with their changes.

  3. Who is responsible if your software does not do what it promises to do?
  
    No one, the authors or copyright holders are not liable if their software does not do what it promises.
  
  **GPL-3:**
  
  1.The GPL-3 license has anyone can modify the work as long as they release the source code for everything that uses the original work, state their source, and document the changes they have made.

  2.  Distributors of software under the patent can charge for them if they wish.

  3. The license states that "there is no warranty for this free software," so my guess is no one is liable.
  
  **LGPL-3:**
  
  1.  The LGPL requires source code release of only those components that are modifications of the original, otherwise its the same as the above.

  2.Derivative works can be used to make a profit.

  3. The authors or copywrite holders of the original work are not liable if the software does not do what it promises.
  
  **CC-0:**
  
  1. Under the Creative Common license, anyone can do anything with the original work.

  2.Anyone can use the original or derivative works for making a profit.

  3. No one is liable if it does not do what is is supposed to. 
    
3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I think some of the considerations that I would beed to think of is who will use the package that I make. I think that GPL-3 is a good licience to use because you are still getting credit for the work that you are doing. If I have made a package, I know that I want it to be able to used in the accademic atmosphere, as bettering code is really important, but I dont really want to have to give code releases as in the LGPL licence. Plus I dont really want to be liable if something is messed up. Thus I think that GPL is the best licence accademiccally. 





## Instructions:

Update your forked version of the 'blog-2019' repository (or re-fork it after deleting your previous repo).

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*. (Note: Lastname = your family name, Firstname = your given name)

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post! 

Once you are done, **create a pull request** to upload your changes to the original repository. Do not commit the compiled HTML file to the repository.
