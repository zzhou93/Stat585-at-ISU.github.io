---
title: "All that legal stuff..."
author: "Weiquan Luo"
topic: "07"
layout: post
root: ../../../
---



#### 1. Under what license does R operate?

  According to the [R project](https://www.r-project.org/Licenses/), R uses `GPL-2` or `GPL-3`
  
#### 2. Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.

  Three of the main questions to answer are: 

  Q1.Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
  Q2.Are you and your collaborators fine with other people making a profit from those derivations?
  
  Q3.Who is responsible if your software does not do what it promises to do?

|Licenses |[MIT](https://tldrlegal.com/license/mit-license)| [GPL-3](https://tldrlegal.com/license/gnu-general-public-license-v3-(gpl-3))| [LGPL-3](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.en.html)| [CC-0](https://tldrlegal.com/license/creative-commons-cc0-1.0-universal)| 
|---------------|---------------|---------------|---------------|---------------|
|Q1: Modifying & Sharing|Yes, users has free permission to deal in the software without restriction, including modifying, distributing, and selling the software. However, must include the copyright notice and te license notice in all copies or substantial uses of the work|Yes, it is a `copyleft` licenses, so distributes modified versions (derivative works) must also make the source code available |NOT ok with others distributing modified versions of the work. Change is not allowed without specific attribution to the authors. If modify, the original function should remain as it is, and the modified versions must follow rules similar to GPL-3 |Yes, it can be freely used by anyone for any purpose|
|Q2: Profit|Yes|Yes|No. The modified work is licensed at no charge to all third parties|Yes|
|Q3: Authors' responsibility|user is liable for any malfunctions|user is liable for any malfunctions|user is liable for any malfunctions|user is liable for any malfunctions |

#### 3. Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.

suppose I am working in my advisor's project funded by National Science Fundation. I use R to analyze data obtain from USDA, which are consider property in public domain. Since I was working in Iowa State University, So All my publication within this project is ISU property, However, the package I create for the analysis in R, so I also need to make the source code avaliable according to GPL-3 or relative licenses.
